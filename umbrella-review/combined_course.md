# An Advanced Practice Nurse's Guide to Umbrella Reviews in R

This course provides a practical, hands-on introduction to conducting umbrella reviews using the R programming language. It is designed for doctoral advanced practice nurse (DNP) students and clinicians who are new to R but experienced in evidence-based practice.

Over four modules, you will move from installing R to producing a complete, publication-ready umbrella review analysis.

## Course Structure

- **01_Module_Foundations**: Setting up your R environment and understanding the 'why' behind using code for evidence synthesis.
    - **01_Assignment_Setup**
- **02_Module_Data_Wrangling**: The essential skills of importing, cleaning, and preparing your dataset for analysis using the `tidyverse`.
    - **02_Assignment_Data_Cleaning**
- **03_Module_The_Umbrella_Review**: Performing the core meta-analytic calculations and generating key visualizations like forest and funnel plots.
    - **03_Assignment_Meta_Analysis**
- **04_Module_Communicating_Findings**: Creating polished, publication-quality tables and figures to clearly present your results.
    - **04_Assignment_Reporting**

## Learning Objectives

Upon completing this course, you will be able to:
1.  Demonstrate basic proficiency with the R and RStudio environment, including installing and loading packages.
2.  Load a dataset, perform essential cleaning and transformation steps, and prepare it for analysis.
3.  Conduct a complete umbrella review analysis, including calculating summary effects and assessing heterogeneity.
4.  Generate, interpret, and customize key tables and figures for reporting and publication.

## Data

The sample dataset for the assignments is located at `data/umbrella_data.csv`.

---

# Module 1: Foundations

**Objective:** To install and orient you to the R and RStudio environment and introduce the core concepts of reproducibility in research.

---

## 1.1 Why R for an Umbrella Review?

As nurse leaders, the credibility and reliability of our research are paramount. While you can perform an umbrella review manually, this approach has significant drawbacks.

- **Manual methods** are prone to error, are difficult to document precisely, and make it challenging for others (or your future self) to replicate your work.
- **R**, on the other hand, is a free, powerful programming language built for statistical analysis. By writing a script, you create a perfect, reproducible record of every step of your analysis.

**The benefits of using R:**
- **Reproducibility:** Anyone can re-run your script and get the exact same results. This is the gold standard in modern research.
- **Transparency:** Your script is a clear and unambiguous methods section.
- **Power & Flexibility:** R has thousands of 'packages' (add-ons) that can perform nearly any statistical analysis imaginable, including specialized methods for meta-analysis.
- **High-Quality Visuals:** R can produce stunning, publication-quality graphics.

## 1.2 Your Toolkit: R and RStudio

You need two pieces of software:
1.  **R:** The underlying programming language. Download it from the [Comprehensive R Archive Network (CRAN)](https://cran.r-project.org/).
2.  **RStudio:** An Integrated Development Environment (IDE) that makes R much easier to use. It's like a smart workbench for your R projects. Download the free Desktop version from [Posit](https://posit.co/download/rstudio-desktop/).

**Install R first, then RStudio.**

### The RStudio Interface

When you open RStudio, you'll see four main panes:
1.  **Top-Left (Source):** This is your text editor, where you will write and save your R scripts (`.R` files). This is where your reproducible record lives.
2.  **Bottom-Left (Console):** This is where R actually executes commands. You can type commands here directly, or 'run' them from your script above.
3.  **Top-Right (Environment/History):** The Environment tab shows you all the 'objects' (like datasets or variables) that you have created in your current R session.
4.  **Bottom-Right (Files/Plots/Packages):** This multi-purpose pane lets you see files in your project directory, view plots you create, and manage packages.

## 1.3 The Building Blocks of R

### Objects and the Assignment Arrow `<-`
In R, everything is an 'object'. You create objects by assigning a value to a name. The assignment arrow `<-` is used for this. Think of it as "gets".

```r
# Create an object named 'x' that gets the value 5
x <- 5

# Create an object named 'study_name' that gets a character string
study_name <- "Smith et al., 2021"
```

### Functions `()`
Functions are how you *do things* in R. A function takes 'arguments' inside the parentheses `()` and returns a result.

```r
# The function c() combines values into a vector
my_sample_sizes <- c(102, 350, 245)

# The function mean() calculates the average of those numbers
mean(my_sample_sizes)
```

### Packages: R's Superpower
Packages are collections of functions and data that extend R's capabilities. For our course, we will use a few key packages:

- `tidyverse`: A powerful collection of packages for data manipulation and visualization.
- `meta`: A user-friendly package for conducting meta-analyses.
- `gt`: For creating beautiful, publication-ready tables.

You install a package **once** using `install.packages()`.

```r
install.packages("tidyverse")
install.packages("meta")
install.packages("gt")
```

After installing, you must load the package in every new R session using `library()`.

```r
library(tidyverse)
library(meta)
library(gt)
```

---

This module has set the stage. You now understand the benefits of R and have the basic vocabulary to start working with it. The next step is to get your hands dirty in the first assignment.

---

# Assignment 1: Your First R Script

**Objective:** To ensure your R environment is correctly set up and to practice the fundamental concepts of creating a script, installing packages, and loading them.

---

## Instructions

1.  **Install R and RStudio:** If you have not already, install R and then RStudio from the links provided in the Module 1 lecture notes.

2.  **Create a New R Script:**
    -   Open RStudio.
    -   Go to `File > New File > R Script`.
    -   A blank script editor will open in the top-left pane.

3.  **Save the Script:**
    -   Immediately save the script. Go to `File > Save As...`.
    -   Save it in a sensible location with the name `my_first_script.R`.
    -   Good practice is to create a project folder for this course.

4.  **Write Your Code:**
    -   In the script file, type the R code below. Add comments to your code using the `#` symbol to explain what each part does. This is a crucial habit for reproducibility.

    ```r
    # Assignment 1: My First R Script
    # Student Name: [Your Name Here]
    # Date: [Current Date]

    # --- Part 1: Installing and Loading Packages ---

    # Install the key packages we will use for the course.
    # You only need to run this install command once.
    # If you have already installed them, you can comment out these lines.
    install.packages("tidyverse")
    install.packages("meta")
    install.packages("gt")

    # Load the packages into our current R session so we can use their functions.
    # You will do this every time you start a new R script.
    library(tidyverse)
    library(meta)
    library(gt)


    # --- Part 2: Creating Objects ---

    # Create a numeric vector object containing the number of participants
    # from five hypothetical systematic reviews.
    participant_counts <- c(453, 1200, 890, 2450, 675)

    # Create a character vector object with the names of the lead authors.
    authors <- c("Jones", "Kim", "Al-Jamil", "Garcia", "Sinclair")


    # --- Part 3: Using a Function ---

    # Use the print() function to display the objects you created in the console.
    print(participant_counts)
    print(authors)

    # Use a statistical function, sum(), to calculate the total number of
    # participants across all five reviews.
    total_participants <- sum(participant_counts)

    # Print the total.
    print(total_participants)

    ```

5.  **Run Your Code:**
    -   To run a single line, place your cursor on that line and press `Cmd+Enter` (on Mac) or `Ctrl+Enter` (on Windows).
    -   Observe what happens in the Console (bottom-left) and Environment (top-right) panes.
    -   You can also highlight a block of code and run it all at once.

## Submission

There is no formal submission for this assignment. The goal is to successfully run the entire script without errors. If your script runs, you have successfully configured your environment and are ready for Module 2.

**Troubleshooting:**
-   If you get an error like `could not find function "library"`, it means you may have a typo or R has not started correctly.
-   If `install.packages()` fails, you may have an internet connection issue or firewall blocking the connection to CRAN.
-   Remember, R is case-sensitive! `library(Tidyverse)` will fail; it must be `library(tidyverse)`.

---

# Module 2: Data Wrangling with the Tidyverse

**Objective:** To learn how to import, clean, and transform a dataset into a format ready for meta-analysis. This is often the most time-consuming, but most critical, part of any data analysis project.

---

## 2.1 Tidy Data

The `tidyverse` is a collection of R packages designed for data science that share an underlying philosophy. At its core is the concept of **"tidy data"**:
1.  Every column is a variable.
2.  Every row is an observation (in our case, a single study).
3.  Every cell is a single value.

Your data extraction spreadsheet should follow this format. For an umbrella review, a tidy dataset might have columns like `author`, `year`, `n_total` (total sample size), `effect_estimate`, `ci_lower` (lower confidence interval), `ci_upper` (upper confidence interval), etc.

## 2.2 Reading Your Data

Most likely, your data is in a CSV (Comma-Separated Values) or Excel file. The `readr` package (part of the `tidyverse`) is perfect for this.

```r
library(tidyverse)

# Read a CSV file into an R object called 'raw_data'
# The file should be in your RStudio project directory or a subfolder (e.g., 'data')
raw_data <- read_csv("data/umbrella_data.csv")

# Always look at the first few rows to make sure it loaded correctly
head(raw_data)
```

## 2.3 The Pipe Operator: `%>%`

The pipe operator is a game-changer for readability. It takes the object on its left and passes it as the *first argument* to the function on its right.

**Without the pipe:**
```r
filter(raw_data, year > 2015)
```

**With the pipe:**
```r
raw_data %>% filter(year > 2015)
```
This may seem trivial now, but it allows you to chain multiple actions together in a logical, readable sequence. `data %>% do_this %>% then_do_that %>% then_finish_with_this`.

## 2.4 The Core `dplyr` Verbs

`dplyr` is the data manipulation grammar of the `tidyverse`. You can handle 90% of data cleaning tasks with a few key "verbs" (functions).

### `filter()` - Keep rows that meet a condition.
Let's say you only want to include studies published after 2010, or those that used a specific measurement tool.

```r
# Keep studies published after 2010
studies_after_2010 <- raw_data %>%
  filter(year > 2010)

# Keep studies that are randomized controlled trials (RCTs)
rct_studies <- raw_data %>%
  filter(study_design == "RCT")

# Combine conditions: RCTs published after 2010
modern_rcts <- raw_data %>%
  filter(year > 2010 & study_design == "RCT")
```

### `select()` - Choose columns by name.
Your raw data sheet might have lots of extra columns. `select()` lets you focus on what you need.

```r
# Select only the columns needed for analysis
analysis_data <- raw_data %>%
  select(author, year, effect_estimate, ci_lower, ci_upper)
```

### `mutate()` - Create new columns.
This is arguably the most powerful verb. You can use it to perform calculations and create new variables. For meta-analysis, we often have an effect estimate (like an Odds Ratio) and confidence intervals, but the functions need the **log-transformed effect** and the **standard error (SE)**.

`mutate()` is how we calculate these.

```r
# Let's say our data has OR, CI.lower, and CI.upper
# We need to calculate log(OR) and the standard error from the CIs.
# The formula for SE on the log scale is: (log(upper_ci) - log(lower_ci)) / 3.92
prepared_data <- raw_data %>%
  # First, remove studies with missing data needed for the calculation
  filter(!is.na(effect_estimate) & !is.na(ci_lower) & !is.na(ci_upper)) %>%
  mutate(
    # Calculate the log-transformed effect estimate
    log_effect = log(effect_estimate),

    # Calculate the standard error from the confidence intervals
    se_log_effect = (log(ci_upper) - log(ci_lower)) / 3.92
  ) %>%
  # Let's keep only the columns we need going forward
  select(author, year, log_effect, se_log_effect)

# Look at the new, prepared data
head(prepared_data)
```
*Note: The `is.na()` function checks for missing values, which is a common and important cleaning step.*

---

With these few functions (`read_csv`, `filter`, `select`, `mutate`), you have the power to take a messy, complex spreadsheet and turn it into a clean, tidy, analysis-ready dataset. The next assignment will put these skills into practice.

---

# Assignment 2: Data Cleaning in Practice

**Objective:** To apply your `tidyverse` data wrangling skills to import a messy dataset and prepare it for meta-analysis.

---

## The Scenario

You have received a CSV file (`umbrella_data.csv`) containing data extracted from several systematic reviews on the effect of a new educational intervention on patient compliance. However, the data is messy. Your task is to clean it and create a new, "tidy" data frame that is ready for the meta-analysis in Module 3.

A preview of the raw data (`umbrella_data.csv`) can be found in the `data` sub-directory of this course.

## Instructions

1.  **Create a New R Script:**
    -   In RStudio, create a new R script and save it as `data_cleaning.R`.

2.  **Write Your Cleaning Script:**
    -   Follow the steps below, adding code to your script for each one.
    -   Use the pipe `%>%` to chain your steps together.
    -   Add comments to explain your logic.

    ```r
    # Assignment 2: Data Cleaning Script
    # Student Name: [Your Name Here]
    # Date: [Current Date]

    # --- Part 1: Load Packages and Data ---

    # Load the tidyverse package
    library(tidyverse)

    # Read the provided CSV file into an object called 'raw_studies'
    # Make sure the 'umbrella_data.csv' file is in a 'data' subfolder
    # relative to your R script, or provide the full path.
    raw_studies <- read_csv("data/umbrella_data.csv")

    # --- Part 2: Clean the Data ---

    # Create a new object called 'cleaned_studies'.
    # This will be the result of a chain of cleaning steps.
    cleaned_studies <- raw_studies %>%

      # Step 1: Filter for relevant studies.
      # Only keep studies that are "RCT"s and where the outcome is "Compliance".
      # Some studies are case-control and some measured a "Knowledge" outcome.
      filter(study_design == "RCT", outcome == "Compliance") %>%

      # Step 2: Handle missing data.
      # The meta-analysis function will need 'or', 'ci_low', and 'ci_high'.
      # Remove any rows where these values are missing (NA).
      filter(!is.na(or) & !is.na(ci_low) & !is.na(ci_high)) %>%

      # Step 3: Create the necessary variables for meta-analysis.
      # The 'meta' package needs the log-transformed effect and its standard error.
      mutate(
        # TE is the 'Treatment Effect' on the log scale
        TE = log(or),

        # seTE is the 'Standard Error of the Treatment Effect' on the log scale
        # Calculate it from the confidence intervals: (log(upper) - log(lower)) / 3.92
        seTE = (log(ci_high) - log(ci_low)) / 3.92
      ) %>%

      # Step 4: Select and rename columns for clarity.
      # We only need author, year, and our newly created variables.
      # Let's also rename 'n' to 'sample_size' to be more descriptive.
      select(
        author,
        year,
        sample_size = n,
        TE,
        seTE
      )

    # --- Part 3: Verify Your Work ---

    # Print the first few rows of your new, cleaned data frame to the console.
    print(cleaned_studies)

    # You can also save your cleaned data to a new CSV file. This is great practice.
    write_csv(cleaned_studies, "data/cleaned_umbrella_data.csv")

    ```

3.  **Run the script and check your output.** The `cleaned_studies` object in your Environment pane should have fewer rows than `raw_studies` and contain the new `TE` and `seTE` columns. It should only have the 5 columns you specified in the `select()` step.

## Submission

Like the first assignment, the goal is to successfully run the script. If it runs without errors and produces a `cleaned_studies` data frame that looks correct, you are ready for Module 3.

**Challenge (Optional):**
- Can you add another `mutate()` step to create a "label" column that combines the author and year? (Hint: look up the `paste()` or `str_glue()` functions). This is very useful for plots.
- For example: `label = str_glue("{author}, {year}")`

---

# Module 3: The Umbrella Review

**Objective:** To conduct the meta-analysis using the `meta` package and to generate and interpret the fundamental visualizations of meta-analysis: the forest plot and the funnel plot.

---

## 3.1 The `meta` Package

Now that we have a clean, analysis-ready dataset, we can finally perform the meta-analysis. The `meta` package is a powerful and user-friendly tool for this. We will use the `metagen()` function, which stands for "meta-analysis, generic inverse variance." This method is appropriate because we have the log-transformed treatment effect (`TE`) and its standard error (`seTE`) for each study.

## 3.2 Performing the Meta-Analysis

The syntax for `metagen()` is straightforward. You provide the dataset and specify which columns correspond to the treatment effect, its standard error, and the study labels.

```r
# First, ensure you have your cleaned data from Module 2.
# If you are starting a new script, you'll need to load packages and the data.
library(tidyverse)
library(meta)

cleaned_studies <- read_csv("data/cleaned_umbrella_data.csv") %>%
  # Let's add the study label we discussed in the last assignment for better plots
  mutate(study_label = str_glue("{author}, {year}"))


# Now, run the meta-analysis
meta_analysis_results <- metagen(
  TE = TE,                       # Column with the (log) Treatment Effect
  seTE = seTE,                   # Column with the Standard Error of the TE
  data = cleaned_studies,        # The data frame containing the data
  studlab = study_label,         # Column with the study labels for plots
  sm = "OR",                     # The summary measure: "OR" for Odds Ratio
  method.tau = "REML",           # A standard method for estimating heterogeneity
  prediction = TRUE,             # Generate a prediction interval
  random = TRUE                  # Use a random-effects model (almost always correct for umbrella reviews)
)

# To see a detailed summary of the results in the console:
summary(meta_analysis_results)
```

## 3.3 Interpreting the Output

The `summary()` output gives you everything you need:

-   **List of studies:** Shows the individual effect estimates you provided.
-   **Number of studies:** `k = ...`
-   **Summary Effect (Random Effects Model):** This is your main result! It will show the pooled Odds Ratio and its 95% confidence interval.
-   **Quantifying Heterogeneity:**
    -   **tau²:** The variance of the true effect sizes across studies.
    -   **I² (I-squared):** The percentage of total variation across studies that is due to heterogeneity rather than chance. This is very important.
        -   `I² < 40%`: Might be low heterogeneity
        -   `I² 40%-60%`: Moderate heterogeneity
        -   `I² > 60%`: Substantial heterogeneity
-   **Prediction Interval:** This interval shows the likely range of true effects in *future* studies. If your summary CI is `[1.2, 1.8]` but your prediction interval is `[0.9, 2.5]`, it suggests that while the *average* effect is positive, a future study could plausibly find no effect. This is a crucial concept for clinical interpretation.

## 3.4 The Forest Plot

A picture is worth a thousand words, and the forest plot is the iconic visualization of a meta-analysis.

```r
# Generate the forest plot
forest(meta_analysis_results)
```
The plot shows:
-   Each study's effect estimate (a square) and its confidence interval (a horizontal line). The size of the square is proportional to the study's weight in the analysis.
-   A diamond at the bottom representing the pooled summary effect and its confidence interval.
-   A vertical "line of no effect" (at 1.0 for Odds Ratios). If a CI crosses this line, the result is not statistically significant. If the diamond crosses it, the overall summary effect is not statistically significant.

## 3.5 Assessing Publication Bias: The Funnel Plot

Publication bias occurs when studies with statistically significant results are more likely to be published than those with null or negative results. A funnel plot helps visualize this.

```r
# Generate the funnel plot
funnel(meta_analysis_results)
```

In the absence of bias, the plot should resemble a symmetrical, inverted funnel. The points (studies) should be scattered evenly on both sides of the summary effect line. If there is a suspicious gap—for instance, an absence of small, non-significant studies in the bottom-left corner—it may suggest publication bias.

---

You have now completed the core analytical steps of an umbrella review. You've calculated a summary effect, quantified the heterogeneity between studies, and assessed for potential publication bias. The next step is to put these skills to the test.

---

# Assignment 3: Performing Your First Meta-Analysis

**Objective:** To use the `meta` package to conduct a meta-analysis on your cleaned data, generate the key plots, and begin to interpret the results.

---

## Instructions

1.  **Create a New R Script:**
    -   Start a new R script and save it as `meta_analysis.R`.
    -   Your script should begin by loading the necessary packages and the cleaned data file you created in Assignment 2 (`cleaned_umbrella_data.csv`).

2.  **Write Your Analysis Script:**
    -   Follow the steps outlined below. Remember to comment your code!

    ```r
    # Assignment 3: Meta-Analysis Script
    # Student Name: [Your Name Here]
    # Date: [Current Date]

    # --- Part 1: Setup ---

    # Load the required packages
    library(tidyverse)
    library(meta)

    # Load the cleaned dataset you created in Assignment 2
    cleaned_studies <- read_csv("data/cleaned_umbrella_data.csv")


    # --- Part 2: Prepare Labels ---

    # For professional-looking plots, we need good study labels.
    # Create a new column 'study_label' that combines author and year.
    # The str_glue() function from the stringr package (part of tidyverse) is great for this.
    analysis_data <- cleaned_studies %>%
      mutate(study_label = str_glue("{author}, {year}"))


    # --- Part 3: Conduct the Meta-Analysis ---

    # Use the metagen() function to perform the random-effects meta-analysis.
    # Store the results in an object called 'm1'.
    m1 <- metagen(
      TE = TE,
      seTE = seTE,
      data = analysis_data,
      studlab = study_label,
      sm = "OR",             # We are summarizing Odds Ratios
      prediction = TRUE,     # We want to see the prediction interval
      random = TRUE          # We assume studies are not identical, so we use a random-effects model
    )


    # --- Part 4: Review and Visualize the Results ---

    # Print the detailed summary of the meta-analysis to the console.
    # This is where you'll find the I-squared, p-values, etc.
    summary(m1)

    # Generate a forest plot and save it.
    # First, let's open a PNG device to save the plot directly to a file.
    png("figures/forest_plot.png", width = 10, height = 8, units = "in", res = 300)
    forest(m1,
           leftcols = c("studlab", "sample_size"), # what to show on the left
           rightcols = c("effect.ci", "w.random"), # what to show on the right
           print.tau2 = TRUE,
           print.I2 = TRUE
           )
    # Close the PNG device to finish saving.
    dev.off()


    # Generate a funnel plot to check for publication bias.
    png("figures/funnel_plot.png", width = 8, height = 8, units = "in", res = 300)
    funnel(m1)
    dev.off() # Close the device


    ```

3.  **Create a `figures` directory:** The code above saves plots to a `figures` subfolder. You will need to create this folder in your project directory for the script to work.

4.  **Run the script and answer the following questions.**
    -   Look at the output of `summary(m1)` in your console.
    -   Examine the saved plots in the `figures` folder.

## Interpretation Questions

Based on the output of your script, write down the answers to these questions (you can add them as comments in your R script).

1.  How many studies (`k`) were included in the final meta-analysis?
2.  What is the summary Odds Ratio and its 95% Confidence Interval? Is the result statistically significant?
3.  What is the I² value? How would you classify the level of heterogeneity (low, moderate, substantial)?
4.  Look at the Forest Plot. Which study had the largest effect size? Which study had the most weight (i.e., the largest square)?
5.  Look at the Funnel Plot. Does it appear to be symmetrical? Do you have any concerns about publication bias based on this visual inspection?

---

Successfully answering these questions means you have not only run the analysis but are also beginning to interpret it in a clinically and statistically meaningful way. You are ready for the final module on communication.

---

# Module 4: Communicating Your Findings

**Objective:** To transform your R analysis outputs into professional, publication-ready tables and figures suitable for a manuscript or presentation.

---

## 4.1 Beyond the Basic Plot

The default plots in R are good for initial analysis, but for publication, you need more control over titles, labels, and appearance.

### Customizing a Forest Plot
The `forest()` function has many arguments to make your plot look more professional. You can add titles, change labels, and control what information is displayed.

```r
# Load your meta-analysis object 'm1' if you don't have it in your environment
# ...

# Create a more detailed forest plot
forest(m1,
       studlab = TRUE,
       comb.fixed = FALSE, # We don't need to show the fixed-effect result
       comb.random = TRUE,
       leftcols = c("studlab", "n", "effect.ci"),
       rightcols = FALSE,
       smlab = "Summary of Studies (Odds Ratio)", # Label for the x-axis
       overall.hetstat = TRUE,
       print.I2 = TRUE,
       print.tau2 = TRUE,
       col.square = "navy", # Change the color of the study squares
       col.diamond = "maroon" # Change the color of the summary diamond
)
```
*Tip: Type `?forest.meta` in the console to see a help file with all possible customization options.*

## 4.2 Publication-Quality Tables with `gt`

A "Table 1" summarizing the characteristics of included studies is standard in any review. The `gt` package creates beautiful, highly customizable tables from your data frames.

Let's create a summary table from our `analysis_data` object.

```r
# Make sure you have the 'gt' package and your 'analysis_data' loaded
library(gt)
library(tidyverse)

# analysis_data <- read_csv("data/cleaned_umbrella_data.csv") %>%
#   mutate(study_label = str_glue("{author}, {year}"))

# Let's add the original OR and CIs back for the table
table_data <- analysis_data %>%
  left_join(read_csv("data/umbrella_data.csv") %>% select(author, year, or, ci_low, ci_high)) %>%
  select(study_label, sample_size, or, ci_low, ci_high)

# Create the table with gt
summary_table <- table_data %>%
  gt() %>%
  # Add a title and subtitle
  tab_header(
    title = "Table 1: Characteristics of Included Studies",
    subtitle = "RCTs Evaluating an Educational Intervention for Patient Compliance"
  ) %>%
  # Rename columns for clarity
  cols_label(
    study_label = "Study",
    sample_size = "Sample Size",
    or = "Odds Ratio",
    ci_low = "Lower 95% CI",
    ci_high = "Upper 95% CI"
  ) %>%
  # Format numbers to two decimal places
  fmt_number(
    columns = c(or, ci_low, ci_high),
    decimals = 2
  ) %>%
  # Add a source note
  tab_source_note(
    source_note = "Data extracted from primary systematic reviews."
  )

# To view the table
summary_table
```
You can save this table to a file (e.g., PNG or Word) using the `gtsave()` function.

```r
# gtsave(summary_table, filename = "figures/table_1.png")
# gtsave(summary_table, filename = "figures/table_1.rtf") # For Word
```

## 4.3 Bringing It All Together: R Markdown (Optional Next Step)

While this course focuses on R scripts, the ultimate tool for reproducible research is **R Markdown**. An R Markdown document (`.Rmd`) allows you to weave together narrative text (like your manuscript introduction and methods), R code chunks, and the output they produce (tables and figures) into a single, perfectly formatted document (e.g., Word, PDF, or HTML).

This is beyond our current scope, but know that everything you've learned is a direct stepping stone to using R Markdown for maximum efficiency and reproducibility.

---

## Course Conclusion

Congratulations! You have completed a full, end-to-end umbrella review analysis in R. You have moved from a raw data file to a set of publication-ready results, and you have a script that documents your entire process.

**You have learned to:**
1.  Set up and use the RStudio environment.
2.  Install and load packages.
3.  Import and clean data using `tidyverse` principles.
4.  Perform a random-effects meta-analysis with `metagen`.
5.  Interpret summary effects, heterogeneity, and prediction intervals.
6.  Generate and interpret forest and funnel plots.
7.  Create high-quality tables and customize figures for communication.

These skills are a powerful foundation for conducting rigorous, reproducible, and transparent research in your DNP program and beyond.

---

# Assignment 4: Communicating Your Findings

**Objective:** To create a publication-quality summary table and a customized forest plot from your meta-analysis results.

---

## Instructions

This final assignment pulls together everything you have learned. You will create two key outputs for a final manuscript: a "Table 1" summarizing the studies and a polished forest plot.

1.  **Create a New R Script:**
    -   Start a new R script and save it as `reporting.R`.
    -   Your script should begin by loading all necessary packages (`tidyverse`, `meta`, `gt`) and the data/objects from previous steps.

2.  **Write Your Reporting Script:**
    -   Follow the steps below.

    ```r
    # Assignment 4: Reporting Script
    # Student Name: [Your Name Here]
    # Date: [Current Date]

    # --- Part 1: Setup ---

    # Load all required packages
    library(tidyverse)
    library(meta)
    library(gt)

    # Re-create your analysis data and meta-analysis results from previous assignments.
    # It is good practice to have all steps in one place for the final report.

    # 1a. Load and clean raw data
    analysis_data <- read_csv("data/umbrella_data.csv") %>%
      filter(study_design == "RCT", outcome == "Compliance", !is.na(or)) %>%
      mutate(
        TE = log(or),
        seTE = (log(ci_high) - log(ci_low)) / 3.92,
        study_label = str_glue("{author}, {year}")
      ) %>%
      select(study_label, author, year, sample_size = n, TE, seTE)

    # 1b. Run the meta-analysis
    m1 <- metagen(
      TE = TE,
      seTE = seTE,
      data = analysis_data,
      studlab = study_label,
      sm = "OR",
      prediction = TRUE,
      random = TRUE
    )


    # --- Part 2: Create a Publication-Ready Table 1 ---

    # Join your cleaned analysis data with the original raw data to get the OR and CIs back
    table_1_data <- analysis_data %>%
      left_join(
        read_csv("data/umbrella_data.csv") %>% select(author, year, or, ci_low, ci_high),
        by = c("author", "year")
      ) %>%
      select(study_label, sample_size, or, ci_low, ci_high) %>%
      arrange(study_label) # Sort the table alphabetically

    # Use the gt() package to format the table
    table_1 <- table_1_data %>%
      gt() %>%
      # Add a header
      tab_header(
        title = "Table 1: Summary of Included Studies",
        subtitle = "Randomized Controlled Trials of an Educational Intervention"
      ) %>%
      # Add a final summary row for the total sample size
      summary_rows(
        columns = sample_size,
        fns = list(Total = "sum"),
        formatter = fmt_number,
        decimals = 0
      ) %>%
      # Clean up column labels
      cols_label(
        study_label = "Study",
        sample_size = "N",
        or = "OR",
        ci_low = "95% CI Lower",
        ci_high = "95% CI Upper"
      ) %>%
      # Format numbers
      fmt_number(columns = c(or, ci_low, ci_high), decimals = 2) %>%
      # Add a footnote
      tab_source_note(md("OR = Odds Ratio; CI = Confidence Interval."))

    # Save the table to a file in your 'figures' directory
    gtsave(table_1, filename = "figures/Table_1_Final.rtf")


    # --- Part 3: Create a Polished Forest Plot ---

    # Open a PNG device to save the plot
    png("figures/Forest_Plot_Final.png", width = 12, height = 8, units = "in", res = 300)

    # Create the forest plot with customizations
    forest(
      m1,
      leftcols = c("studlab", "sample_size"),
      rightcols = c("effect.ci", "w.random"),
      col.predict = "red",
      print.I2 = TRUE,
      print.tau2 = TRUE,
      smlab = "Odds Ratio (95% CI)",
      weight.study = "random",
      hetstat = TRUE,
      overall.hetstat = TRUE,
      col.square = "royalblue",
      col.diamond = "darkred",
      main = "Effect of Educational Intervention on Patient Compliance"
    )

    # Close the PNG device
    dev.off()
    ```

## Submission and Final Product

Run your `reporting.R` script. It should execute without errors and produce two files in your `figures` directory:
1.  `Table_1_Final.rtf`: A rich-text file you can open in Microsoft Word or another word processor. It should be a beautifully formatted table.
2.  `Forest_Plot_Final.png`: A high-resolution image of your customized forest plot, ready to be inserted into a manuscript.

Review these two files. Do they look professional? Are they easy to interpret?

If so, you have successfully created a reproducible, publication-ready analysis. You have demonstrated mastery of the course objectives.
