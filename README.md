### Local alignment using the Smith-Waterman algorithm ###

The Smith-Waterman algorithm is an algorithm used for local alignment of two genome sequences. The algorithm is used to calculate the optimum alignment, using a gap penality (w) and match/mismatch score (ms/mms) of choice. Using the algorithm, you generate a scoring matrix (H) for your alignment which has the dimesions of your two sequences, having the length of i (sequence 1) and j (sequence 2). Any position in the scoring matrix will be called <img src="https://render.githubusercontent.com/render/math?math=$H_{i,j}$ ">. <br>

The positions around a specific position are used to determine the value for the specific position. Of interest, are the values in the left position, in the above position and in the above left position. These are called <img src="https://render.githubusercontent.com/render/math?math=$H_{i,j-1}$ ">, <img src="https://render.githubusercontent.com/render/math?math=$H_{i-1,j}$ ">, <img src="https://render.githubusercontent.com/render/math?math=$H_{i-1,j-1}$ ">, respectively (Wikipedia 2020). 

To find the value of <img src="https://render.githubusercontent.com/render/math?math=$H_{i,j}$ ">, you look at the bases you want to align in the specific position. These bases can either form a match or a mismatch if you move diagonally, which will give different scores. This score can sometimes be low (if it's a mismatch), which will make it likely that a gap in the allignment, would give a higher score in the end. Therefore, the assigned value in the specific position is:

<img width="295" alt="Screenshot 2021-06-25 at 18 22 18" src="https://user-images.githubusercontent.com/70690268/123456252-ed919b80-d5e2-11eb-9abb-3cb134cd6046.png">

0 is also included, so that the scoring cannot be negative. This is what makes the alignment local. The value of <img src="https://render.githubusercontent.com/render/math?math=$s(a_{i},b_{j})$ "> is determined by whether the two bases (a and b), that have to align, are a match or a mismatch (Wikipedia 2020):  

<img width="263" alt="Screenshot 2021-06-25 at 18 22 24" src="https://user-images.githubusercontent.com/70690268/123456289-f97d5d80-d5e2-11eb-806b-67ae314e55b3.png">


The maximum values are calculated for all positions in the scoring matrix. The scoring matrix is then used to find the optimal alignment. The optimal alignment is the alignment with the highest score. The first thing you do is find the highest score, and then you backtrack from this position, going back through the same route, that were used for the scoring. If for example <img src="https://render.githubusercontent.com/render/math?math=$H_{i-1,j}-w_{1}$ "> gave the value in the current position, then you have to go to the above position next, being <img src="https://render.githubusercontent.com/render/math?math=$H_{i-1,j}$ ">. This way you continue backwards in the scoring matrix until the value of your position is 0. Then you have your finished local alignment. 

### User information

The input sequences are in a fasta format, and the resulting alignment(s) are stored in an excel file in a path of the user's choice. This path can be edited in the top of the script ("path_"). The user can change the parameters of the function, with a match score, mismatch score, and gap penalty (linear) of own choice. The fasta file can be changed in the top of the script ("path"), and sequence names can also easily be changed, as long as the squence names are in upper case letters. The resulting excel file contains two rows, one with the letters of sequence 1 and one with letters of sequence 2, aligning correctly. If there is a gap, it will be marked with "-".


### References

SciPy. (2019a). numpy.zeros. Retrieved from <br>
https://docs.scipy.org/doc/numpy/reference/generated/numpy.zeros.html <br>
SciPy. (2019b). numpy.ndarray.shape. Retrieved from <br>
https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.shape.html <br>
thispointer.com. (2018a). Find max value & its index in Numpy | numpy.amax(). Retrieved from <br> https://thispointer.com/find-max-value-its-index-in-numpy-array-numpy-amax/ <br>
thispointer.com. (2018b). Find the index of value in Numpy Array using numpy.where(). Retrieved from <br> https://thispointer.com/find-the-index-of-a-value-in-numpy-array/<br>
Wikipedia. (2019). FASTA format. Retrieved from <br> https://en.wikipedia.org/wiki/FASTA_format <br>
Wikipedia. (2020). Smith-Waterman algorithm. Retrieved from<br> https://en.wikipedia.org/wiki/Smith–Waterman_algorithm <br>
Willems, K. (2016). Pandas Cheat Sheet for Data Science in Python. Retrieved from <br>https://www.datacamp.com/community/blog/python-pandas-cheat-sheet?utm_source=adwords_ppc&utm_campaignid=898687156&utm_adgroupid=48947256715&utm_device=c&utm_keyword=&utm_matchtype=b&utm_network=g&utm_adpostion=1t1&utm_creative=332602034349&utm_targetid=aud-392016246653:dsa-473406587915&utm_loc_interest_ms=&utm_loc_physical_ms=1005016&gclid=Cj0KCQiApaXxBRDNARIsAGFdaB8EsguOi1R2Y9eBOe0jsvlTmp82xOs3w7Pd3o4sETVQMqiiHeAyskMaAkxbEALw_wcB
