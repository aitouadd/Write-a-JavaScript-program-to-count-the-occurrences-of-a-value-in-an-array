# Write-a-JavaScript-program-to-count-the-occurrences-of-a-value-in-an-array






This tutorial will teach you how to count the number of occurrences of elements in an array. We’ll show you how to do it with Objects, Array.prototype.reduce,         a custom function, and Lodash.
   

    
    
    



# Use Array.prototype.reduce() to increment a counter each time the specific value is encountered inside the array.
    
   
   
   
   
   
 Array.prototype.reduce takes two arguments: a callback function and an initial value. When you set the initial value to an Object, you can set the properties of   this object as the array elements.
   
   
   
   
   
   
   
   
   
   
   
          const countOccurrences = (arr, val) => arr.reduce((a, v) => (v === val ? a + 1 : a), 0);
                  console.log(countOccurrences([1, 1, 2, 1, 2, 3], 1));
                  console.log(countOccurrences([1, 1, 2, 1, 2, 3], 2));
                  console.log(countOccurrences([1, 1, 2, 1, 2, 3], 3)); 
                  
                  
      
  Sample Output:
  
      3
      2
      1
      

# Object-based Approach to Count Occurrences of Array Elements in JavaScript
    
      
      const myArray = [3,2,3,3,5,6,5,5,8,4,4,7,7,7];
      const counts = {};

          for (const num of myArray) {
             counts[num] = counts[num] ? counts[num] + 1 : 1;
          }
      console.log(counts[2], counts[3], counts[4], counts[5], counts[6], counts[7], counts[8]);
      
      
      
      
  Output:
      
      1 3 2 3 1 3 1  
      
      
      
      
 # Use a Custom Function to Count Occurrences of Array Elements in JavaScript
     
 Here is the function algorithm that counts the number of occurrences of array elements.

1.Initialize two empty arrays called A and B.

2.Set up a variable to keep track of a previous element when looping through the array.

3.Clone the array that the function receives as an argument.

4.Sort the cloned array.

5.Loop through the cloned array with a for...of loop. 5.1 If the array element is not equal to the previous element. 5.1.1 Push the element into array A. 5.1.2 Push an
initial value of one into array B. 5.2 Else 5.2.1 Increment the value in array B. 5.2.2 Set the previous element to the current element.

6.Return array A and array B.

  The following code is the implementation of this algorithm.
     
     
     

     
     
     let mArray = [2,3,4,1,2,2,5,3,7,8,1,1,6];

        function countOccurrences(array) {
               let arrayElements 			= [],
               occurrences					= [],
               cloneOriginalArray 	= [...array], 
               previousElement;
             // Sort the cloned array
                 cloneOriginalArray.sort();
            for (let element of cloneOriginalArray) {
                  if (element !== previousElement) { // That means it's a new element
                         arrayElements.push(element); 	// push it into the array
                         occurrences.push(1);					// push its occurence in the occurrence array
            } else ++occurrences[occurrences.length - 1]; // Not a new element, so increment its occurrence
                   previousElement = element;
            }
       	return [arrayElements, occurrences];
      }
      const arrayAndItsOccurrences = countOccurrences(mArray);
      console.log('[' + arrayAndItsOccurrences[0] + ']', '[' + arrayAndItsOccurrences[1] + ']');
      
      
      
   Output: 
      
      [1,2,3,4,5,6,7,8] [3,3,2,1,1,1,1,1]
      
 # Use Lodash to Count Occurrences of Array Elements in JavaScript
 
 
 
   Lodash has the .countBy method that takes an array and returns an object. This object contains the elements in the array and their values as key-value pairs.
          
          
          
          
          
          
        <body>
       	   <script
	              src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.21/lodash.min.js"
	              integrity="sha512-WFN04846sdKMIP5LKNphMaWzU7YpMyCU245etK3g/2ARYbPK9Ub18eG+ljU96qKRCWh+quCY7yefSmlkQw1ANQ=="
                  crossorigin="anonymous"
	              referrerpolicy="no-referrer">
	         </script>
	         <script>
		           let loArray = [2,2,3,3,1,1,5,3,4,4,8,3,2,9];
		           let lodash = _;
		           let occurrences = _.countBy(loArray);
		           console.log(occurrences)
	         </script>
        </body>    
        
        
        
  Output:
        
        Object { 1: 2, 2: 3, 3: 4, 4: 2, 5: 1, 8: 1, 9: 1 }
      
      
      
