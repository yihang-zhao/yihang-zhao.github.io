# Personalized Zodiac Insights Visualization

## Introduction

This project focuses on examining the relationship between Zodiac signs, perceptions of social media influencers, and the impact of social media on shopping behaviors. Complete design and insights could be seen from https://miro.com/app/board/uXjVMVP_Drw=/?share_link_id=14153724503

## Data Processing and Acknowledgements

In this project, I aimed to create an interactive visualization of Zodiac sign insights based on demographic data from various sources. The data processing pipeline involved several crucial steps to ensure the final visualization accurately represents the desired information and relationships.

### 1. Use Python:

1.1 Data extraction and cleaning: The raw dataset contained a diverse range of demographic attributes for participants. I focused specifically on the Zodiac sign groups, extracting relevant rows and simplifying the segment name column by retaining only the Zodiac sign names.

1.2 Data consolidation and categorization: I analyzed and filtered rows from a second dataset containing questions pertaining to the most important traits of influencers. I identified eight distinct answer types and combined similar answers (e.g., 'a famous person' and 'They are famous so people like to follow') into a single category, such as 'Famous person'. I then recalculated the percentages for each answer within each Zodiac sign group to ensure accurate representation.

1.3 Data transformation and hierarchical structuring: To create a sunburst graph for the visualization, I merged the processed datasets and converted them into a hierarchical JSON format. The structure comprised multiple depth levels: depth 0 representing Zodiac signs, depth 1 denoting the four Zodiac elements (Earth, Air, Fire, and Water), depth 2 specifying each Zodiac sign within an element, depth 3 differentiating between social media preferences and influencer preferences, and depth 4 detailing the answer categories for the selected aspect (7 types for influencers and 5 types for social media).

<div style="display: flex; justify-content: center; align-items: center; flex-wrap: wrap;">
  <img src="./data_preprocess/code_snippet_1.jpeg" alt="Image description" style="height: 200px; width: auto;">
  <img src="./data_preprocess/code_snippet_2.jpeg" alt="Image description" style="height: 200px; width: auto;">
  <img src="./data_preprocess/code_snippet_3.jpeg" alt="Image description" style="height: 200px; width: auto;">
</div>

### 2. Use D3:

2.1 Fetch and parse the JSON data:
The getData function fetches data from the 'data/data.json' file using the fetch API and then parses the JSON data using response.json(). This function returns the parsed JSON data.

2.2 Create a hierarchical layout:
D3 uses a partition layout to create a hierarchical structure for the Sunburst chart. The partition layout is created using d3.layout.partition(), and it computes the arc sizes and positions based on the hierarchical data. The layout is configured with a value accessor function that returns the size attribute of each data node.

2.3 Bind the data to DOM elements:
The svg.selectAll("g") line selects all "g" elements within the SVG container, and the data(partition.nodes(root)) binds the hierarchical data nodes (computed by the partition layout) to these elements. The enter().append("g") creates new "g" elements for each data node that doesn't have a corresponding "g" element.

2.4 Create and style the arcs:
Using the data-bound "g" elements, the code appends a "path" element for each data node and sets the "d" attribute using the arc function. The arc function is created using d3.svg.arc() and is configured with start angle, end angle, inner radius, and outer radius. The arcs are also styled with fill colors and event listeners for interactivity.

2.5 Create and style the text labels:
The code appends a "text" element for each data node and positions it using the "x", "dx", "dy", and "transform" attributes. The text content is set using the name attribute of the data node, and the text is styled with fill color, font size, and other properties.

2.6 Interactivity and updates:
The code provides several functions to update the visualization based on user interactions, such as clicking on arcs, changing the color scheme, and adjusting text size. These functions usually involve changing the attributes or styles of the DOM elements based on the updated data or user inputs.

The data used in this project has been collected from various reliable sources and processed to create an insightful and interactive visualization. I'd like to express my gratitude to the following data sources:

1. Social Influence on Shopping: https://data.world/ahalps/social-influence-on-shopping
2. Online Influencer Marketing: https://data.world/ahalps/online-influencer-marketing

### 3. Acknowledgements

I would like to express my gratitude to Adam Halper for providing the two datasets that have been instrumental in this research. These datasets have contributed significantly to the analysis and understanding of the relationship between Zodiac signs, social media influencers, and shopping behaviors.

## Demonstration

Hello everyone, I am excited to introduce my Zodiac Insights Visualization web Application, an interactive exploration of zodiac data related to social media influencers and the impact on shopping behavior across social platforms.

First, we utilized a dataset from data.world, through a pipeline involving extraction and cleaning, merging and categorization, transformation, and stratification, we created a strong foundation for our sunburst chart. The 0th layer of the sunburst chart explains the research subjects, the 1st layer is the four zodiac groups, the 2nd layer is the three zodiac signs within each group, and the 3rd layer is the two research focuses for each zodiac sign: 1. their opinion on media influencers, 2. the social media that influences their shopping behavior. The 4th layer represents the proportion of answers for each research focus, reflecting the characteristics of each zodiac sign. 

Let's discuss the design principles behind the web application. I chose a sunburst chart for visualization because it can intuitively display multi-level data and effectively present the hierarchy and interactivity of the data. Our goal was to create a user-friendly interface, with adaptive and responsive design for four screen sizes, including mobile screens. 

Users can manually adjust the text size or bold the text for easier reading based on their screen size, or revert to the default settings if adjustments are incorrect. 

I ensured my design is accessible to people with different types of color vision deficiencies and provided customization options. Users can choose from colorblind-friendly color schemes, with eight different schemes available for the eight types of colorblindness. I also added transition animations for each button click, giving the customization module a modern aesthetic. 

Now, let's dive into the demonstration of this web application. After exploring a portion of the subcategories, users may be particularly interested in one zodiac group. They can remove all other groups and display only the one they are interested in, using the display all depth button to access information for every member of the group. Users can discover similarities between the characteristics of the three zodiac signs in the group concerning their responses to the research questions, as well as explore whether there is a connection between their views on social media influencers and their susceptibility to the influence of different social media on their shopping behaviour. Afterward, users can add new zodiac groups to explore the differences or similarities between different groups. Finally, by clicking reset view, they can return to the normal interaction mode and begin a new exploration. 

That's my overall design, thank you.

## Features

1. Interactive sunburst chart for easy exploration of the data
2. Personalized visualization toolbar allowing users to filter and customize the chart
3. Colorblindness-friendly color options
4. Dynamic text size and style adjustments for improved accessibility
5. Detailed tooltips displaying specific information for each data point
6. Filter groups to compare at once

