
<!-- README.md is generated from README.Rmd. Please edit that file -->

# predicttornado

<!-- badges: start -->

[![codecov](https://codecov.io/gh/DSCI-310-2024/predicttornado/graph/badge.svg?token=mMPk1l0T8M)](https://codecov.io/gh/DSCI-310-2024/predicttornado)
<!-- badges: end -->

The goal of predicttornado is to provide functions that help with the
data analysis of predicting the number of fatalities using length and
width of tornadoes based on tornado data.

## Functions included

- `process_data`: Removes NA values in `mag` variable and
  repetitive/irrelevant columns from data frame and renames column names
  in a specific order given that original columns in dataset are in the
  correct order.

- `create_scatterplot`: Creates a scatter plot from the provided data
  and specified two numerical columns with specific size, aesthetics,
  and font size settings.

- `boxplot_viz`: Creates a boxplot of a variable of interest where
  outliers or skewed data may be a concern.

- `fit_linear_model`: Creates and fits a linear model to the training
  data with linear regression and returns regression coefficients.

- `accuracy_plot`: Creates a scatter plot from the provided data
  comparing the accuracy of a regression model to the actual
  observations.

## Place within the R package ecosystem

`predicttornado` may seem like a package very similar to other R
packages. For example, we have three visualization functions that
resemble `ggplot2`. However, they are all slightly different and more
tailored to our data analysis project. `create_scatterplot`and
`boxplot_viz` have specific visualization size settings and title and
aesthetics that render your visualizations more pleasing.

Moreover, `accuracy_plot` is very different because even though it uses
`ggplot2` functions, it creates a scatterplot that compares the accuracy
of a linear regression model to the actual observations.

`process_data` is also different from `dplyr`’s `select` and `filter` as
it combines these different functions to create an efficient data
processing function for ease of data analysis. Additionally, it is a
specific processing function for analysis tornado data in predicting
fatalities.

Lastly, `fit_linear_model` is also different from other linear
regression functions such as `lm` from `stats` for example because it
combines multiple steps required in creating and fitting a linear
regression model and then automatically outputs the model coefficient
and intercept.

## Installation

You can install the development version of predicttornado like so:

``` r
# install.packages("devtools")
devtools::install_github("DSCI-310-2024/predicttornado")
```

## Usage

After installing the package, you can use a workflow like the following
to use its functions. Click
[here](https://dsci-310-2024.github.io/predicttornado/articles/predicttornado-vignette.html)
for a more detailed guide on how to use our package functions.

    library(predicttornado)

`process_data`:

    clean_data <- process_data(tornado_df)

`create_scatterplot`:

    width_fatalities_scatterplot <- create_scatterplot(clean_df, width, fatalities) + 
    ggplot2::labs(x = "Width of tornadoes (yards)", y = "Fatalities", 
    title = "Figure 2: Scatterplot of width (yards) of tornado and fatalities")

`boxplot_viz`:

    fatalities_boxplot <- boxplot_viz(clean_df, fatalities)

`fit_linear_model`:

    lm_data <- fit_linear_model(fatalities ~ width + length, clean_df) |>
        predict(clean_df) |>
        bind_cols(clean_df)

`accuracy_plot`:

    fatalities_accuracy_plot <- accuracy_plot(clean_df, fatalities) + 
    labs(x = "Actual Number of Fatalities", y = "Predicted Number of Fatalities")

## Contributors

- Erika Delorme
- Marcela Flaherty
- Riddha Tuladhar
- Edwin Yeung

## Contributing

Do you want to contribute to our package? Check out the [contributing
guidelines](https://github.com/DSCI-310-2024/predicttornado/blob/main/CONTRIBUTING.md).
Please note that this project is released with a [Code of
Conduct](https://github.com/DSCI-310-2024/predicttornado/blob/main/CODE_OF_CONDUCT.md).
By contributing to this project, you agree to abide by its terms.

## License

`predicttornado` was created by Erika Delorme, Marcela Flaherty, Riddha
Tuladhar, and Edwin Yeung. It is licensed under the terms of the [MIT
license](https://github.com/DSCI-310-2024/predicttornado/blob/main/LICENSE.md).
