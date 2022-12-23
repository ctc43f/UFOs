# UFOs

## Overview of the Analysis
For this challenge assignment, we were asked to create an interactive website that allows a user to dynamically filter the entire dataset by entering various values into the filters.  We were provided with a sparse set of HTML and Javascript code and asked to modify such that **the user could key in values for date, city, state, country, or UFO shape and have the data table update accordingly.**

## Results
I was able to successfully update both the .js and .html files to allow the dynamic filtering without having to click a button.

![Image 1: Filters](/Resources/filters.png)

I created the five filters allowing users to key in the results.  I also attempted to indicate in the default text and in the filter description how the user should input the filter values in order to be successful (this will be discussed more in the **Summary** section) because the Javascript code as I created it requires not only an exact match of the text but the case as well.  If the user wanted to filter on sightings in California, he or she must type "ca" into the State filter; entering "CA", "Ca", or "California" will generate a blank table because no table values exactly match these strings.

![Image 2: Results](/Resources/filter_results.png)

To test the filtering, entering "ca" into the State filter reduces the results in the table to just those with an exact match in the corresponding column.  The above screenshot shows the first two rows of results when the filter was applied.

## Summary

### Webpage Drawbacks
There are several drawbacks to the webpage:
1. When the filtered results span more than one screen length, the user is required to scroll down to continue viewing data but the filters are not static.  They will scroll offscreen, requiring the user to scroll back up to further modify.
2. As mentioned above, the filters are case-sensitive and there is no fuzzy logic in the background to offer approximate matches (e.g. "CA" is treated the same as "ca".)
3. Because of the size of the data set, it isn't clear what are valid values for each filter field (range of dates, states included in the data set, etc.)  The text entry fields should instead be dynamic drop-downs with the ability to select multiple items that are valid given whatever other filters have already been applied.
4. There is no quick way to remove all of the applied filters; a "Clear Filters" button would be useful.
5. Once the user has filtered data, there should be a way to export the data to a csv file via button click for further analysis.

### Additional Development Opportunities

In addition to the handful of items and recommendations made in the above section, there is one other one that I would highlight that isn't clear to the end-user but that could be refined in the Javascript.

The below is a snippet of the code I used to compare data values to the filter values and pare down the data accordingly:

[Image 3: For Loop](/Resources/jscode.png) 

I initially attempted to extract the key values from my filters object and then compare to the corresponding column in the data object.  For example, if the user entered "us" into the Country filter, my javascript filters object would be:

```
{country: 'us'}
```
I tried to then extract the 'country' key from the object and compare to the data, but I was not able to figure out how to reference that value specifically.  I tried some indexing (i.e. fitlers[0]) and also tried to extract the key values as a separate array, but was not successful.  I then manually keyed an if statement for each filter.  The main issue with this is that, with the method I attempted, the filtering loop would update automatically (the for loop only cares what columns appear in the filters object, which is controlled by the HTML code adding filters).  With my code currently, it would require the developer to adjust the code every time a filter was added or removed to the page.
