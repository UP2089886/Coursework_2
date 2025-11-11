# Item 1

# **Unix**

## (1) Consider the following code:

	program CW1
	integer i, j, k
	real*8  a(512,512,512)
	open(unit=6, file=’output.txt’, status=’unknown’)
	do i = 1, 512
	  do j = 1, 512
	do k = 1, 512
	      a(i,j,k) = 100 * dexp(pi/2).
	      write(6,*) a(i,j,k)
	enddo enddo
	enddo
	close(unit=6)
	end

### (a) name 3 ways in which this code can be optimised, be specific. (6 marks)
- 1] Changing the looping order from i,j,k to k,j,i makes the program significantly faster due the way it is laid out and accessed in the computers microprocessors. 
- 2] Declaring the $100 \bullet  e^{\frac{\pi}{2}}$ as a value outside the loop rather than adding having the code calculate it over 134 million times. 
- 3] Rewriting the values into the array each time is extremely inefficient, it is faster to add the values into the array in large chunks outside the loop. 

		program CW1
		integer i, j, k
		real*8  a(512,512,512), value, pi
		open(unit=6, file='output.txt', status='unknown')
		pi = 4.0d0 * datan(1.0d0) // found this on reddit
		value = 100 * dexp(pi/2)
		do k = 1, 512
		 do j = 1, 512
			do i = 1, 512
		      a(i,j,k) = value
		      
			enddo 
		 enddo
		 write(6,*) a(i,j,k)
		enddo
		close(unit=6)
		end


### (b) what in addition to (a) can be done to speed this code up at runtime? (2 marks)

- Using a different compiler to optimise the code in a way that is specific to the machine in use. Most typically we would use the "gfortran -02" compiler, as it is the best balance between optimisation and caution. You can use "gfortran -03" or "gfortran -0fast" which both make the code even faster but these tend to be too aggressive for large and complex codes. 
- Use a super computer and assign a processor to each of the i j k directions and then add everything together at the end. Or taking it a step further and having a processor for each chunk of points in each direction of the 3D array. 
### (c) how large in bytes will be the output file? (2 marks)
- if you have each value as a double precision float, each data point takes up 8 bytes of space. $$[8 \ \text{bytes/point}] \bullet [(512 \bullet512\bullet 512) \ \text{points}] = 1073741824 \ \text{bytes} = 2^{30} \ \text{bytes} = 1 \ \text{Giga Byte (GB)}  $$

### (d) the world’s first real supercomputer, the Cray-1 which debuted in 1976, had 170 MB of RAM. Could you have run this code on that machine (why or why not)? (2 marks)


## (2) You want to submit a run with zeusmp.x to Sciama on 512 cores to run for 24 hours. Modify the batch sub- mission script in the supercomputing primer to do this, assuming 16 cores per node and executing an MPI version of the code. (5 marks).

## (3) You have a file containing the following vegetables:

	tomato
	cucumber
	broccoli
	potato
	lettuce
	cabbage
	carrot 
	celery

### (a) what unix command would you use to find ’cucumber’ and print it to the screen? Be efficient. (2 marks)

### (b) what unix command would you use to instead output cucumber to the file ’output.txt’? (2 marks)

### (c) what unix command would you use to add ’cabbage’ to output.txt? (2 marks)

### (d) what unix command would you use to then move output.txt to the directory one level above the current one? (2 marks)

# **Github**

## (4) You are tasked with making a pull request that adds a new feature to some existing code kept in a GitHub repository, what process (workflow) would you follow?  Assume you have already cloned the repository to your local computer. (3)
 
 
## (5) What information should you include in the pull request from the previous question? (2)

