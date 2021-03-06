# nlplot
Visualization Module for Natural Language Processing

## Description
Facilitates the visualization of natural language processing and provides quicker analysis

You can draw the following graph

1. N-gram bar chart
2. N-gram tree Map
3. Histogram of the word count
4. wordcloud
5. co-occurrence networks
6. sunburst chart
7. pyLDAvis

（Tested in English and Japanese）

## Requirement
- [python package](https://github.com/takapy0210/nlplot/blob/master/requirements.txt)

## Install
```sh
pip install nlplot
```

## Usage

sample df

```python
df.head()
```

|    |  text  |
| ---- | ---- |
|  0  |  Think rich look poor |
|  1  |  When you come to a roadblock, take a detour |
|  2  |  When it is dark enough, you can see the stars |
|  3  |  Never let your memories be greater than your dreams  |
|  4  |  Victory is sweetest when you’ve known defeat  |


```python
import nlplot

# taget_col as a list type or a string separated by a space.
npt = nlplot.NLPlot(df, taget_col='text')

# 1. N-gram bar chart
npt.bar_ngram(title='uni-gram', ngram=1, top_n=50)
npt.bar_ngram(title='bi-gram', ngram=2, top_n=50)

# 2. N-gram tree Map
npt.treemap(title='Tree of Most Common Words', ngram=1,top_n=30)

# 3. Histogram of the word count
npt.word_distribution(title='number of words distribution')

# 4. wordcloud
npt.wordcloud()

# 5. co-occurrence networks
npt.build_graph(min_edge_frequency=10)
# The number of nodes and edges to which this output is plotted.
# If this number is too large, plotting will take a long time, so adjust the [min_edge_frequency] well.
>> node_size:70, edge_size:166
npt.co_network(title='Co-occurrence network')

# 6. sunburst chart
npt.sunburst(title='sunburst chart', colorscale=True)

# 7. pyLDAvis
npt.ldavis(num_topics=5, passes=5, save=False)


```

## Document
TBD

## Test
TBD

## Other

- Plotly is used to plot the figure
    - https://plotly.com/python/

- co-occurrence networks is used to calculate the co-occurrence network
    - https://networkx.github.io/documentation/stable/tutorial.html

- The following is used to plot pyLDAvis
    - https://github.com/bmabey/pyLDAvis

- wordcloud uses the following fonts
    - https://mplus-fonts.osdn.jp/about.html