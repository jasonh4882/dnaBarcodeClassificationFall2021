# Submission Method Writeup #

*Jason Hampshire*

For the competition, I only really made one true submission, but the submission I did took many, many painstaking hours to create. For my submission, I created a list of tokens to search for in each DNA sequence and used the results as the features to make a RandomForest model.

For the tokens, I used singlets *(A,T,C,G)*, doublets *(AA, AT, ..., GC, GG)*, triplets *(AAA, AAT, ..., GGC, GGG)*, quartets *(AAAA, AAAT, ..., GGGC, GGGG)*, quintets *(AAAAA, AAAAT, ..., GGGGC, GGGGG)*, and sextets*(AAAAAA, AAAAAT, ..., GGGGGC, GGGGGG)*. Total, this created a list of 5460 features. I was a little worried about overfitting with this many traits, but I do not believe that this ended up being a problem in the end.

To create this list of features, I needed to parse through each of the DNA sequences 5460 times, looking for each of these tokens. I realize that there may have been a more efficient way, but in the moment, this is how I decided to do it. My first attempt can be fount in comp2 notebook. The notebook is non nonfunctional as a whole as I ended up using it as a testing ground later, but I found that is was going to take far too long to get though all of the sequences in both train and test this way.

To help rectify this issue, I decided to look into ways to run the sequences with multithreading. This, by far, was both the best and worst part of this project. I fell into the sunk cost fallacy after I had spent so many nights trying to figure out how to do it and while I did eventually get it working, I spend much much longer doing so than I needed to. 

To start with, the multi threading library I used *(this may not be true with all that are out there)* Could not and would not run in a notebook so i had to resort to writing in a *.py* file instead and executing through either the Jupyter Lab terminal. More commonly, I just ran it in Windows *cmd.exe* in the correct directory.

The library is also very finicky in general. I do appologize if you cannot get it working on your machine. It took hours of troubleshooting to get it working in the first place. At one point, I restarted my computer and when I came back to the project, the file would not run again and I had to spend another hour just to find out that Windows did something wonky and I needed to edit how much virtual memory was available. I also was running the script with Administrator Privledges; I do not know if this mattered, but since I was running it in the Program Files folder, it was necessary for me.

The three files that were used to generate the features were *comp3.py* for 90% of train, *comp4.py* for test, and *comp5.py* for the last 10% of train. I did this so that I could use the last 10% for validation of the model. *comp6.ibynb* is the notebook that I ended up using to actually generate the model once all of the features were compiled.

If you cannot get the files working on your end, here is the first part of the *.py* file printout:

    C:\Program Files\Python39\CSCI 49000\Competition>py comp3.py
    Thread with ID 17944 has been initialized
    CSCI 49000 Deep Learning Competition DNA token Generation
    importing time.time ... done
    
    Preparing token sets...
            singlet tokens...       done
            doublet tokens...       done
            triplet tokens...       done
            quartet tokens...       done
            quintet tokens...       done
            sextet tokens...        done
            Compiling token sets together...        done
    Loading and separating the nucleotide training data...  done
    importing concurrent.futures ...        done
    importing time.sleep ...        done
    
    Creating ProcessPoolExecutor...
    done
    
    Creating Threads...     Thread Startup Check:
            Thread 0:       Process Created
            Thread 1:       Process Created
            Thread 2:       Process Created
            Thread 3:       Process Created
            Thread 4:       Process Created
            Thread 5:       Process Created
            Thread 6:       Process Created
            Thread 7:       Process Created
            Thread 8:       Process Created
            Thread 9:       Process Created
            Thread 10:      Process Created
            Thread 11:      Process Created
            Thread 12:      Process Created
            Thread 13:      Process Created
            Thread 14:      Process Created
            Thread 15:      Process Created
            Thread 16:      Process Created
            Thread 17:      Process Created
            Thread 18:      Process Created
            Thread 19:      Process Created
            Thread 20:      Process Created
            Thread 21:      Process Created
            Thread 22:      Process Created
            Thread 23:      Process Created
    Runtime: 0 Min 1 Sec
    Thread with ID 18288 has been initialized
    Thread with ID 18012 has been initialized
    Thread with ID 18312 has been initialized
    Thread with ID 18048 has been initialized
    Thread with ID 18296 has been initialized
    Thread with ID 18028 has been initialized
    Thread with ID 18068 has been initialized
    Thread with ID 18340 has been initialized
    Thread with ID 18360 has been initialized
    Thread with ID 18232 has been initialized
    Thread with ID 18132 has been initialized
    Thread with ID 18328 has been initialized
    Thread with ID 18392 has been initialized
    Thread with ID 18248 has been initialized
    Thread with ID 18152 has been initialized
    Thread with ID 18400 has been initialized
    Thread with ID 18416 has been initialized
    Thread with ID 18408 has been initialized
    Thread with ID 18172 has been initialized
    Thread with ID 18108 has been initialized
    Thread with ID 18088 has been initialized
    Thread with ID 18268 has been initialized
    Thread with ID 18212 has been initialized
    Thread with ID 18192 has been initialized
    
                    Remaining Futures: #Done:[0]/#ToGo:[11616]              Main Thread Clock Speed:2s
    Worker# 0       1       2       3       4       5       6       7       8       9.       10      11      12      13      14      15      16      17      18      19      20      21      22      23
            Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active
    Active Threads: [24]/[24]
    
    Process #[29]/[11616]:Starting ID# 10708                Process #[2]/[11616] finished by Thread ID #18048
    Runtime: 0:0:8          Remaining Futures: #Done:[24]/#ToGo:[11592]             Main Thread Clock Speed:2.0s
    Worker# 0       1       2       3       4       5       6       7       8       9       10      11      12      13      14      15      16      17      18      19      20      21      22      23
            Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active
    Active Threads: [24]/[24]
    
    Process #[36]/[11616]:Starting ID# 9843                 Process #[24]/[11616] finished by Thread ID #18068
    Runtime: 0:0:13         Remaining Futures: #Done:[48]/#ToGo:[11568]             Main Thread Clock Speed:2.0s
    Worker# 0       1       2       3       4       5       6       7       8       9       10      11      12      13      14      15      16      17      18      19      20      21      22      23
            Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Active  Closed  Closed  Closed  Closed  Closed  Closed  Closed  Closed  Closed  Closed
    Active Threads: [14]/[24]
    

The script ran the method that parsed the sequences in 24 different threads. I chose this many as I have an *i7 8600K CPU* that has 6 cores and 12 logical processors. Having 2 threads per processor seemed to work the best for be but the library will allow up to 62 concurrent threads to be ran.

All of the printouts that this script made were of my creation and the library, *concurrent.futures* was only used specifically for the threading only. Other libraries were used as well for importing and time.

The script would print out when a process was started and finished, but would overwrite the previous line with *'\r'* to reduce the length of the output. the script would also print the status of the beginning of the process queue, which is where the *'Workers'* and *'Active*, *Open*, and *Closed*' is coming from. In the end, this ended up working, being able to generate all 5640 tokens for all of the 20000+ sequences in around 3 hours. By my calculations, if I had let this run normally, It would have taken 3+ days to run.

While this was running, My computer was at max utilization on all 12 processors, making doing much of anything on my computer virtually impossible. I set up a datalogging of my computer to track all of this as well. I have included these in the zipped folder. If opened in Excel, the noteworthy information is in columns *Y to AM*. These showed that all of the cores were pinned to the max for the entire length of the script. This may not mean anything to whoever is grating this, but that is a big deal to me and is something I have never experienced. Thankfully, I have a very overkill comnputer that has an overkill cooling solution so overheating was not a problem. I did not have the memory usage logged, but it was in the *22-24GB* range out of my *32GB* available. I mention all of these things because this would not have been possible to run if I did not have the advantage of a powerful computer and I feel as though that is worth nothing.

In the end, the Random Forest generated in *comp6* yeilded **98.91% accuracy** when trained with the 90% of train and compered to the 10% making me quite comfident that it would preform well in the competition. 