# Module-11-Challenge-UFO

### Resources
- Data source: data.js
- Software/Libraries: JavaScript ES6, D3, HTML5, CSS, Boostrap

### GitHub Page

https://mejikano.github.io/Module-11-Challenge-UFO/index.html


## Overview

 Dana a journalist wants to publish and article relate to UFOs sightings but using a dynamic webpage able to filter based on user criteria, this project uses JavaScript ES6 to accomplish this goal. 



## Results

UFO Sightings page has a table that can be filtered based on users input on the left side text boxes, the table results will dynamically return the records according to the filtering criteria. 

Following example walk the user thru each table filter

1. No Filters - UFO Sightings 

![No Filter - UFO Sightings Table](https://github.com/Mejikano/Module-11-Challenge-UFO/blob/main/static/images/No_filter.png)

2. State Filter - UFO Sightings 

The state of California (CA) is filtered and the table shows provided state result 

![State Filter - UFO Sightings Table](https://github.com/Mejikano/Module-11-Challenge-UFO/blob/main/static/images/filter_State.png)

3. Shape Filter - UFO Sightings 

light shapes are entered and the table shows UFO sightings with light shapes in California State (specified before in the City Filter)

![Shape Filter - UFO Sightings Table](https://github.com/Mejikano/Module-11-Challenge-UFO/blob/main/static/images/filter_Shape.png)

4. City Filter - UFO Sightings 

el cajon City is filtered so the table dynamically shows UFO sightings with light shapes in El Cajon City California State (Shape and City entered before filters the result set)

![City Filter - UFO Sightings Table](https://github.com/Mejikano/Module-11-Challenge-UFO/blob/main/static/images/filter_City.png)

5. Date Filter - UFO Sightings 

January, 4 2010  entered in the filter text file shows results for that date with lights sightings  in El Cajon City California State (Shape and City entered before filters the result set)

![Date Filter - UFO Sightings Table](https://github.com/Mejikano/Module-11-Challenge-UFO/blob/main/static/images/filter_Date.png)


## Summary

### Drawback 

Applying multiple filters to each raw was a challenge indeed, a single if statement linked with all user input text at once does not work because the user can leave blank input texts on the filter pane i.e. city === city & state === state & date === date & shape === shape etc. 

Alternatively an algorithm with an if statement per input text: if (city === city), if (state === state) etc... could solve the problem.  

However the iteration and filtering code implemented dinamycally with two JS fat arrow functions take the filters keys and iterates per table record (row) and each input text (key) to identify records matching given criteria. 

***Pros of this approach** is that this same code snippet works if more fields are added to be filtered as it would be just an HTML change, less code lines are needed as well (no if statement per filtering field).  

***Cons of this approach** record is iterated input filter text times, so if city and shape are entered same record will run one iteration for city check and a second iteration for shape check. The good, iterations occurs vs filtered records based on the previous iteration filtering; and performance (at least with this dataset volume) is pretty good.

For Reference below JS code snippet: 
```
    //This array stores all the filters being entered by the user to perform filtering
    filter_keys = Object.keys(filters);
    
    //For each filter key input by user. 
    //Note: if column filters increase it would adjust dinamycally
      filter_keys.forEach((key)=>{
        //Start filtering data iterating row by row
        filteredData = filteredData.filter(row => {
        //if the row key value matches the filter value criteria return the row
          if(row[key] === filters[key]){
            return row
          //console.log(`key:${key}, row_val:${row[key]}, filter_val:${filters[key]}`);
        }
        });
      });
```

### Further development  

Recommendations for future:

- Apply a Calendar Date Picker for dates filters, this will ensure that users enter right dates and formats.
- Use dropdown list instead of text boxex for the rest of the filters, these can be updated dynamically using JS D3 to show to the user just the available values based on previous filtering and the filtered records field values. 