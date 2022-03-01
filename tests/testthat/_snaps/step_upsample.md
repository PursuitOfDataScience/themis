# ratio deprecation

    Code
      new_rec <- recipe(~., data = circle_example) %>% step_upsample(class, ratio = 2)
    Condition
      Error:
      ! The `ratio` argument of `step_downsample()` was deprecated in themis 0.2.0 and is now defunct.
      Please use the `over_ratio` argument instead.

# bad data

    Code
      rec %>% step_upsample(x) %>% prep()
    Condition
      Error in `check_column_factor()`:
      ! `x` should be a factor variable.

---

    Code
      rec %>% step_upsample(class, id) %>% prep()
    Condition
      Error in `step_upsample()`:
      ! The selector should select at most a single variable

# empty printing

    Code
      rec
    Output
      Recipe
      
      Inputs:
      
            role #variables
         outcome          1
       predictor         10
      
      Operations:
      
      Up-sampling based on <none>

---

    Code
      rec
    Output
      Recipe
      
      Inputs:
      
            role #variables
         outcome          1
       predictor         10
      
      Training data contained 32 data points and no missing data.
      
      Operations:
      
      Up-sampling based on <none> [trained]
