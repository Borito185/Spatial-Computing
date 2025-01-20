# Shaping the Building

Once a bounding shape is established, we convert it into a voxel cloud with a 3-meter resolution.
This was determined to offer the optimal balance between resolution and computational efficiency,
allowing all room dimensions to be divisible by 3 meters.

## The building growth 'Algorithm'

### Development Methodology

Our primary objective was to ensure the architectural viability of the structure.
For that reason, we decided to forgo the "voxel by voxel" approach, and construct the shape in groups of voxels in a "
room by room" fashion

Rather than devising a single, definitive algorithm, we adopted
an [agile-like](https://en.wikipedia.org/wiki/Agile_software_development) development methodology.
This involved identifying our requirements, developing the algorithm accordingly, and then engaging in a cycle of
analysis and refinement.
As a result, we were able to quickly prototype with different ideas in mind,
but the final building growth algorithm, although viable, has room for improvement (for example, optimizing the
Gallery for increased sunlight exposure and reducing wind penetration).

## Simplified Building Growth Algorithm

### Starting Selection

We initiate the building growth process by identifying 'starting points' for each unit type.
We can designate the origins from which the units will commence their growth within a configuration file.
2 First floors were manually designated as "Public space".

### Growth step

1. At each step, every starting point evaluates its ability to place a unit at its current location. This determination
   hinges on the availability of sufficient unoccupied space and adequate sunlight on the unit's façade. Should this
   attempt prove unsuccessful, the algorithm will attempt to reposition.
2. If the previous step succeeds, the algorithm will evaluate, whether there is enough space for a 9 meter-wide buffer
   space and a second unit across the newly placed unit.
    - If there is enough space, a 9 meter-wide buffer space will be placed.
    - Otherwise, a 3-meter wide buffer space will be placed
3. Step one is repeated to place a unit on the opposite side of the buffer space.
4. Afterward, new staring points will be selected next to the newly placed unit.
5. If there is no viable space for growth on the current floor, 'starting points' will be selected on the floor above in
   a similar manner to the *Starting Selection* step.
6. The steps are repeated until a predetermined number of units are placed.

### Final result of the growth process {collapsible="true"}

- Green - Elderly units
- Yellow - Family units
- Purple - Student units
- Pink - Buffer space
- Grey - Public space

![showcase_1.png](showcase_1.png)

![showcase_2.png](showcase_2.png)

## Variables and Variations

### Variables

The following variables can be found and modified in `src\assets\data\growth_data.csv`

| Variable name             | Default value | Description                                                                          |
|---------------------------|---------------|--------------------------------------------------------------------------------------|
| elderly_units_needed      | 200           | Number of elderly units needed                                                       |
| family_units_needed       | 200           | Number of family units needed                                                        |
| student_units_needed      | 50            | Number of student units needed                                                       |
| elderly_cluster_x         | -294          | Preferred starting point location for elderly units                                  |
| student_cluster_x         | -372          | Preferred starting point location for student units                                  |
| family_cluster_x          | -337          | Preferred starting point location for family units                                   |
| elderly_min_floor         | 2             | Floor, at which elderly units start growing (upwards)                                |
| student_min_floor         | 11            | Floor, at which student units start growing (upwards)                                |
| family_min_floor          | 2             | Floor, at which family units start growing (upwards)                                 |
| family_and_student_cutoff | -315          | Highest x value, from which student and family units can grow                        |
| student_cutoff            | -370          | Highest x value, from which student units can grow                                   |
| student_thinning          | 1             | when set to 1, the algorithm will limit the student unit growth to 4 units per floor |        

### Additional constraints on elderly unit growth

The team decided to limit the horizontal and vertical spread of the elderly units.
For that reason, elderly units can grow in a point *i*, as long as:

```tex
\begin{equation}
{|x_{i} - elderly\_cluster_x| + y_i^{0.6} } \lt 32
\end{equation}
```

### Different Variations of the Growing Algorithm {collapsible="true"}

Access to multiple adjustable variables and short computation times allowed the team to generate multiple variations of the building

![Zrzut ekranu 2024-01-29 011659.png](Zrzut_ekranu_2024-01-29_011659.png)

![Zrzut ekranu 2024-01-29 012025.png](Zrzut_ekranu_2024-01-29_012025.png)

![Zrzut ekranu 2024-01-29 013616.png](Zrzut_ekranu_2024-01-29_013616.png)

![Zrzut ekranu 2024-01-29 012224.png](Zrzut_ekranu_2024-01-29_012224.png)

![Zrzut ekranu 2024-01-29 013016.png](Zrzut_ekranu_2024-01-29_013016.png)

![Zrzut ekranu 2024-01-29 012840.png](Zrzut_ekranu_2024-01-29_012840.png)

![Zrzut ekranu 2024-01-29 012545.png](Zrzut_ekranu_2024-01-29_012545.png)