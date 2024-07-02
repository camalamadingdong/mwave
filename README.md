# mwave
`mwave` is a water wave and wave energy converter (WEC) computation package written for MATLAB.
Copyright (C) 2014  Cameron McNatt
contact: cameron.mcnatt@gmail.com
repository: https://github.com/cmcnatt/mwave

README Last modified: 7 July, 2020

## About
`mwave` can be used to compute (for example):
- various linear wave fields
- WEC motions and power
- WEC array motions and power
- WEC wave fields 

At this point, it is essentially all linear wave theory. Most values are complex variables and assume an `exp(i*omega*t)` time dependence, where `i` is the imaginary `1`, `omega` is the radial frequency and `t` is time.

It was initially written as a pre- and post-processor for WAMIT (www.wamit.com), but it has expanded a bit beyond that, for example to include:

- the computation of analytical wave fields (heaving and surging point sources).
- the hydrobody computation, which allows for analytical wave field to be computed from real geometries (albeit with WAMIT).
- the interaction theory computation, which allows for arrays for floating bodies to be computed efficiently. 

The documentation (`Documentation` folder and source files) is still a bit sparse, and this needs work. I would recommend checking out the references (References in `Documentation` folder) including the WAMIT theory manual for more info on the theory. 

I'm sure there are bugs and better ways of doing things than I've implemented. And so, please contribute to the code! If you contribute to a given file, add your name to the header. If you create a new file, add the header, by either copying and pasting the header from the file `mwaveHeader` in the `Header` folder, or by running `addMwaveHeader` on that file. Then submit a GitHub pull request.

## DEPENDENCIES

 - MATLAB (2019b)
 - WAMIT (must be installed in `C:\\wamitv7\`)

## INSTALLATION:
1. Put the `mwave` folder where ever you'd like it.
2. Add it to your MATLAB path, by 
	
	a. running in MATLAB:

	```matlab
	addpath(genpath(folderName),'-frozen')
	savepath
	```

	b. adding to your startup.m file:

	```matlab
	addpath(genpath(folderName),'-frozen')
	```
 
 where folderName is the full path to the `mwave` folder. Because `'-frozen'` is used, MATLAB won't recognize when you add a new file, so be sure to explicitly add that file as well (or run addpath again).

3) Add `newmodes.dll`, see NEWMODES below.

## NEWMODES:
The Newmodes.dll is a library of user defined subroutines that WAMIT uses to compute generalized modes of motion. WAMIT comes with some prewritten subroutines, but I've added some custom ones as well.

The attenuator floating bodies (`FloatingAttenuator`, `FloatingSphereEndCyl`, `FloatingSphereEndCylHinge`) use WAMIT generalized modes. Custom subroutines were written for the WAMIT `Newmodes.dll`.  

At this point, the jury is still out on whether I can share my `Newmodes.dll` or `Newmodes.f` fortran source code, and so unfortunately, unless you write your own version of my subroutine, you cannot run the WAMIT runs with these geometries.
 

## GETTING STARTED:
The best place to get started is with the examples in the `Examples` folder. I tried to very explicit with my comment here. The `UnitTest` folder also has some good examples.

I would really like to make this code as useful to people as possible, so if you have any questions or need help, please contact me at cameron.mcnatt@gmail.com
