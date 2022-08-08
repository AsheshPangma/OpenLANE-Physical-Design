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


`set ::env(FP_IO_MODE) 2`

Placement layout with IO mode 2 |  Zoomed in figure
:-------------------------:|:-------------------------:
![](Day2/placement_FPIOMODE_2.png)  |  ![](Day2/placement_FPIOMODE_2_2.png)











# Day 3 Design Library Cell using Magic Layout and ngspice characterization

At first, we clone the standart inverter cell from repository provided in github to our openlane folder. The command is given below:

`git clone https://github.com/nickson-jose/vsdstdcelldesign.git`


## CMOS inverter using Magic

To view the inverter layout in Magic, we first copied the sky130A.tech file to our vsdstdcelldesign directory. Then, the following script is used to view the inverter layout.

`magic -T Sky130A.tech sky130_inv.mg &`

![](Day3/magic_inv_cmd.png)

![](Day3/inv_layout.png)

### Extractiong SPICE netlist from standard cell layout

`extract all`


`ext2spice cthresh 0 rthresh 0
 ext2spice`
 
 Spice extraction             |  Inverter scale
:----------------------------:|:-------------------------:
![](Day3/spice_extraction.png)  |  ![](Day3/box_inv.png)
 
![](Day3/vim_ngspice.png)

![](Day3/vim_ngspice_2.png)

`vim sky130_inv.spice`

### Transient analysis using NGSPICE

`ngspice sky130_inv.spice`

`ngspice 1 -> plot y vs time a`

![](Day3/ngspice_invoke_2.png)


The waveform shows the inpput and output of inverter w.r.t. time. We can calculate various timing parameters such as rise time delay, fall time delay and propagation delay of the inverter.

![](Day3/plot_y_vs_time_a.png)

The following timing values are obtained from the plot at different values of input and output.

![](Day3/timing_values.png)

# Day 4 Pre-Layout Timing Analysis and Importance of Good Clock Tree



```
<layer-name> <X-or-Y> <track-offset> <track-pitch>
```

![](Day4/track.png)

By using the following command we obtain the grid when viewing layout in Magic.
`grid 0.46um 0.34um 0.23um 0.17um`

 Spice extraction             |  Inverter scale
:----------------------------:|:-------------------------:
![](Day4/inv_grid.png)            |  ![](Day4/inv_grid_2.png)

![](Day4/inv_mag.png)

![](Day4/mag_lef.png)

 Spice extraction             |  Inverter scale
:----------------------------:|:-------------------------:
![](Day4/info_area.png)       |  ![](Day4/info_cell.png)

 Spice extraction             |  Inverter scale
:----------------------------:|:-------------------------:
![](Day4/merged_lef.png)      |  ![](Day4/placement_inv.png)




![](Day4/placement_inv_2.png)

![](Day4/run_cts_prep.png)

```
run_cts
```

![](Day4/run_cts.png)

A file *picorv32a.synthesis_cts.v* is created in the results/synthesis directory


![](Day4/presta.png)

![](Day4/mybase.png)

![](Day4/slack.png)

![](Day4/net_replace.png)

![](Day4/net_replace_2.png)

![](Day4/net_replace_3.png)



# Day 5






# Day 6


























