![docDingDong300](./img/docDingDong300.png)

# Create iEFI Hang Radar SOP

May 22, 2020

Authors:
Anna Ning         Anna.Ning@quantacn.com

# Content

[TOC]

# UNIT Hang/Stack/Panic Process Flow

```flow
st=>start: UNIT Hang/Stack/Panic
e=>end: Event Finish
op1=>operation: CoreOS coredump action and check the unit
cond1=>condition: is iEFI issue?
others1=>operation: Need CoreOS to do
op3=>operation: Create radar and upload coredump
op4=>operation: Reflow unit
st->op1(right)
op1->cond1(yes)->op3->op4->e
cond1(no,right)->others1->op4->e
```



# How to Create an iEFI Hang Radar?
## Steps
<img src="./img/create_radar.png" alt="create_radar" style="zoom:30%;" />

## Radar Description
### Title
```
* Project+Stage+station+online/offline+DTI+result:SN+failure brief description
```
### Component
```
* Factory Test Stations | Project
    Example: Factory Test Stations | PGY
```

### Classification
```
* Choose "Crash/Hang/Data Loss"
```
### Reproducibility
```
* Choose according to the actual situation
    Always/Sometimes/Rarely/Unable/D'dn't Try/Not Applicable
```

### Description
```
* SUMMARY
  1. Recap the problem title and/or include more descriptive summary information.

* STEPS TO REPRODUCE
  1. Setup or prep work
  2. Include explicit and accurate steps to reproduce. Do not include extraneous or irrelevant steps.

* RESULTS
  1. Describe your results and how they differed from what you expected.

* REGRESSION
  1. Provide information on steps taken to isolate the problem. Describe circumstances where the problem 
  2. occurs or does not occur, such as software versions and/or hardware configurations.

* NOTES
  1. Document any additional information that might be useful in resolving the problem, such as references to related problems, leads on diagnosis, screen shots, included attachments, and any workarounds.
```
## Attachments (are included in CoreDump)

```
* Coredump
* Sysdiagnose
* Astro_full_log
* Other logs as shown in the following pictures
```

![folder_1](./img/folder_1.png)

![folder_2](./img/folder_2.png)