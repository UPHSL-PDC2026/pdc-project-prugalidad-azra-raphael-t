### Problem Description

  The program is to do at least three operations, which is to Filter, Aggregate, and Sort the given data. Here, I have chosen the PHIVOLCS Earthquake reports from 2016 to 2026 to be processed. The data is to then be processed in two different ways: Sequential processing and Parallel processing. Sequential is self-explanatory: in the context of this program, it processes the data by individually looking at the rows and comparing them to the requirements needed, which in this case is a Magnitude >= 4. Parallel processing however, divides the data into different chunks for each individual thread to process on their own, thus parallel.

  The results remained the same despite each different way of processing.

### Parallelization Approach

  In this approach, I used ThreadPoolExecutor. I set the max_workers to 4 threads, as I noticed that the more threads I use beyond 12, the slower it becomes. This is because my CPU, a Ryzen 5 5600, only has 6 cores, meaning it can only properly support 12 threads. Though above 12 threads is possible, it is not supported because of the limited amount of cores, which is the reason why the program slows down enough to be noticed.

  Using chunks = np.array_split(df, 4), I split the dataset into 4 different parts for each of the 4 threads to process the data individually. The line of code is:
  with ThreadPoolExecutor(max_workers=4) as executor:
      chunk_results = list(executor.map(process_data, chunks))

  Where process_data is the function for actually processing the data (Filtering, Aggregating, and Sorting) and chunks = np.array_split(df, 4) to individually process the data. The processed chunks are then concatenated, and then sorted out using the finalize_and_sort function.

### Performance Analysis

  With 4 threads available, the average speed-up of multithreading processing compared to sequential processing is around a 1.7 speed-up time. On average, the sequential processing takes around 0.250 seconds in average, multithreading processing may take as short as 0.143 seconds, which is the lowest I have recorded. It is a 1.9x improvement over sequential processing.

### Challenges Encountered

  The challenges is regarding the approach of parallelization. The sequential processing was simple, simply calling the two functions one by one with the different processes' results. When it comes to parallelization however, it took quite a while to figure out considering how simple it was.

  Another challenge I encountered was how to simplify the multithreading version and to compress it into a smaller program. I did this by strictly programming it for one specific data file, which is the PHIVOLCS earthquake reports csv file. This was done to ensure that the code is and simple to run. Overall, the program itself is challenging to figure out as multithreading is still new to me.
