## Introduction to SEML
SEML: A Simplified English Modeling Language for Constructing Biological Models in Julia
SEML compiler is a code generator that transforms simplified English description of biological network into modeling written in a runnable programming language, such as the [Julia](http://julialang.org), [Python](https://www.python.org) and [Matlab](https://www.mathworks.com/products/matlab.html).
See our [Github webpage](https://zzp12.github.io/SEML.jl/) 

## Requirement 
In order to use SEML, the user needs to [install Julia](https://julialang.org/downloads/platform.html) first. This version is compatible with [Julia v1.1.0](https://julialang.org/downloads/index.html).
The following Julia packages are required: 
* [GLPK](https://github.com/JuliaOpt/GLPK.jl)
* [ODE](https://github.com/JuliaDiffEq/ODE.jl)
* [PyPlot](https://github.com/JuliaPy/PyPlot.jl) 

It can be installed by running in Julia: 

```
using Pkg
]
(v1.1) pkg> add GLPK ODE PyPlot
```


## Installation 


Within [Julia](http://http://julialang.org), use the `clone` command of the package manager to download and install the POETs repository:

```
Pkg.clone("https://github.com/ZZP12/SEML.jl.git")
```

To delete the JuPOETs package use the command:

```
]
(v1.1) pkg> rm SEML
```



## Usage 
To use POETs in your project simply issue the command:

```
using SEML
make_model(arg1[, OutPath=arg2, Host=arg3, Model=arg4, Lang=arg5])

```

The ``make_model.jl`` command takes four arguments:

Argument | Required | Default | Description | options 
--- | --- | --- | --- | ---
arg1 | Yes| none | Path to input file | 
OutPath | No	| ./autogeneratedmodel | Path to where files are written | 
Host | No	| bacterial | Host type  | (bacterial \| mammalian)
Model | No | Kinetics| model type | FBA \| FVA \| Kinetics
Lang | No | julia | programming language | (julia \| python \| python2 \| python3 \| matlab)

## Output Files 
### in Julia 
FBA/FVA model files: 

file | description 
--- | ---
DataDictionary.jl | contains all data of the model, including flux bounds, species concentration bounds, and objective coefficients, etc.   
FluxDriver.jl  |  interface with GLPK solver to run FBA 
FVA.jl  |  implementation of fastFVA from [gudmundsson2010computationally](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-11-489) 
InputFile | SEML description of the model 
include.jl | contains all the include statements for the project.  
Solve.jl | interface to run the simulation 
stoichiometry.dat  | Stoichiometric matrix of the model  
Utility.jl  |  provide some auxiliary functions  

Kinetic model files: 

file | description  
--- | ---
Balances.jl | encodes mass balance of the model 
DataDictionary.jl | contains all data of the model, including initial condition, kinetic constants and Monod affinity constants, etc.   
InputFile | SEML description of the model 
include.jl | contains all the include statements for the project.  
Kinetics.jl | calculates kinetic rates 
SolveBalances.jl | interface to run the simulation  
stoichiometry.dat  | Stoichiometric matrix of the model   

### in Python 
### in Matlab

## Support or Contact

Having trouble at installation or function? Feel free to contact the [authors](https://github.com/varnerlab).
