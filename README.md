# Advanced-Physica-Design-using-openLANE/Sky130

This repository contains all the steps performed in 5-day Advanced-Physica-Design-using-openLANE/Sky130 workshop. This workshop is focused in complete RTL2GDS flow using openLANE flow which is open source flow.

# Table of Contents

# Day 1 - Exploring Open-source Tools, OpenLANE Flow and Sky130 Pdk

## Open source PDK structure

![](Day1/pdk_dir_structure.png)

## Initalizing OpenLANE
In Linux Ubuntu, to invoke OpenLANE, we should first run docker everytime. In our case, we invoke OpenLANE in openlane directory. The script is as follow:
`docker`

There are two modes of operation for OpenLANE: interactive and autonomous.
To invoke openLANE run `./flow.tcl`.
In our workshop, We use interactive mode by running `./flow.tcl -interactive`

After invoking openLANE, we import package required for openLANE of the required version. We use version 0.9.
![](Day1/openlane_invoke.png)

The next step is to prepare our design for OpenLANE flow. We use *picorv32a* in this workshop. Thus, the following command is:
`prep -design picorv32a`

![](Day1/prep_design.png)

The technology LEF and cell LEF files are merged  to obtain a merged.lef file during design preparation stage. The LEF files holds various informations of the design such as layer informations, design rules and also information regarding each standard cells necessary for place and route.

![](Day1/merged.png)

## Design synthesis 

We perform RTL synthesis of our prepared design(picorv32a) by using the following command:
```
run_sunthesis
```

![](Day1/synthesis.png)

The following results are optained.

![](Day1/synthesis_result.png)
![](Day1/synthesis_result2.png)

Chip area = 147792.9184

Number of cells = 14876

Number of flops = 1613

Then, Flop count = Number of cells /over Number of flops = 0.1084 

Buffer count = 1656+8 = 1662

Then, Buffer ratio = Buffer count/ Number of cell = 1662/14876 = 




# Day 2 Floorplan and Introduction to library cell

## Floorplan using OpenLANE

![](Day2/floorplan_setup.png)

![](Day2/floorplan_conf.png) 

![](Day2/conf_tcl.png)

![](Day2/sky130_conf_tcl.png)

The following command is used run Floorplan in OpenLANE:
```
run_floorplan
```
![](Day2/run_floorplan.png)

After running floorplan, we obtain picorv32a.floorplan.def file in results/floorplan directory.

![](Day2/run_floorplan_success.png)

### Floorplan Layout in Magic

![](Day2/floorplan_magic_cmd.png)

![](Day2/floorplan_magic_layout.png)

![](Day2/floorplan_magic_layout_2.png)

![](Day2/floorplan_magic_layout_3.png)





## Placement

## Placement using OpenLANE


![](Day2/placement_setup.png)



```
run_placement
```
![](Day2/placement_run.png)

### Placement Layout in Magic

![](Day2/placement_magic_cmd.png)

![](Day2/placement_layout_magic.png)

![](Day2/placement_magic_layout_2.png)

![](Day2/placement_magic_layout_3.png)


:-------------------------:|:-------------------------:
![](Day2/placement_magic_layout_2.png)  |  ![](Day2/placement_magic_layout_3.png)













# Day 3



# Day 4

# Day 5


























