Item 1

**unix**

(1) Consider the following code:

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

(a) name 3 ways in which this code can be optimized, be specific. (6 marks)

(b) what in addition to (a) can be done to speed this code up at runtime? (2 marks)

(c) how large in bytes will be the output file? (2 marks)

(d) the world’s first real supercomputer, the Cray-1 which debuted in 1976, had 170 MB of RAM. Could you have run this code on that machine (why or why not)? (2 marks)


(2) You want to submit a run with zeusmp.x to Sciama on 512 cores to run for 24 hours. Modify the batch sub- mission script in the supercomputing primer to do this, assuming 16 cores per node and executing an MPI version of the code. (5 marks).

(3) You have a file containing the following vegetables:
tomato
cucumber
broccoli
potato
lettuce
cabbage
carrot 
celery

(a) what unix command would you use to find ’cucumber’ and print it to the screen? Be efficient. (2 marks)

(b) what unix command would you use to instead output cucumber to the file ’output.txt’? (2 marks)

(c) what unix command would you use to add ’cabbage’ to output.txt? (2 marks)

(d) what unix command would you use to then move output.txt to the directory one level above the current one? (2 marks)

**Github**

(4) You are tasked with making a pull request that adds a new feature to some existing code kept in a GitHub repository, what process (workflow) would you follow?  Assume you have already cloned the repository to your local computer. (3)
 
 
(5) What information should you include in the pull request from the previous question? (2)
 
