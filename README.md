# GPCRmodule3

This module is the following of G.Launay's modules, so it is necessary to install and run his modules first.

Documents for module 1 and 2:

	[pyproteins module](https://github.com/glaunay/pyproteins)
	
**Some notes on Installation**

	Step 1. ```source venv/bin/activate`
			source venv/bin/activate```
			
	Step 4. ```export PYTHONPATH="\$VIRTUAL_ENV/modules:$PYTHONPATH"
			export PYTHONPATH="$VIRTUAL_ENV/modules:$PYTHONPATH"```

## Module 3 set up

**Change your working directory**

You can choose to create a new directory or using the same folder **GPCR/venv/modules/**

`cd your/directory`

**Retrieve module's source files from git**

NOTE: This section has to be perform on local machine, not on migale server.

* Initiate git

`git init`

* Clone repo from git

`git clone https://github.com/NguyenLien/GPCRmodule3.git`

A folder name **GPCRmodule3** containing necessary source files will be cloned into working directory.

## Module 3 configuring

Configuration file is provided in venv/modules/module3/module/conf/confModule3.json.
However, this file is not completed. Only templates library is available, other arguments are on the way ...
```{

    "envVariables": null, 
    
    "executable": null, 
    
    "modellerDir": [
    
        "/home/maiage/tplnguyen/Documents/GPCR/test_usage_module_1/Threading2/models"
        
    ], 
    
    "templateDir": [
    
        "/home/maiage/tplnguyen/Documents/GPCR/testmodule2/templates"
        
    ], 
    
    "templateLibrary": {
    
        "or1g1_human_1u19a_03": "/home/maiage/tplnguyen/Documents/GPCR/test_usage_module_1/Threading2/models/hhAlign_1/OR1G1_HUMAN.B99990003.pdb", 
        
        "or1g1_human_1u19a_08": "/home/maiage/tplnguyen/Documents/GPCR/test_usage_module_1/Threading2/models/hhAlign_1/OR1G1_HUMAN.B99990008.pdb", 
        
        "or1g1_human_2rh1a_05": "/home/maiage/tplnguyen/Documents/GPCR/test_usage_module_1/Threading2/models/hhAlign_0/OR1G1_HUMAN.B99990005.pdb", 
        
        "or1g1_human_2rh1a_07": "/home/maiage/tplnguyen/Documents/GPCR/test_usage_module_1/Threading2/models/hhAlign_0/OR1G1_HUMAN.B99990007.pdb"
        
    }
    
}
```
* modellerDir: the folder containing your output folder of pyproteins.

* templateDir: the folder that you want to store all templates (templates database).

* templateLibrary: the list of templates name and their original address.

This file can be created by running `jsontest.py` (modify modellerDir and templateDir), but this file has to be ran after creating templates database (Usage 1).

## Usage

1. Creating templates database.

Basically, this script will search and parse **doModel.log** file produced by **pyproteins** module, extract the 2 best models and copy them into **templateDir**.

```
cd your/directory/GPCRmodule3/docking
python template.py
```

2. Running AutoDock4

**Requirements:** Ligand file in .pdb or .pdbqt

Change your directory into **/GPCRmodule3/bin** or use the **full** path.

```
python module3.py -l "/path/to/ligand/6m5h2o.pdbqt" -c "/path/to/config/confModule3.json" --workDir "/path/to/output/folder" --selectedTemplates "or1g1_human_1u19a_03"
```

Type `python module3.py -h` to see available options.

