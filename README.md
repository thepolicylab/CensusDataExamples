# Grabbing Census Data

This repository contains some standard things you might want to
grab from the Census.

## How to use these examples

The examples are all in Jupyter notebooks using Python. You will need to
have at least those requirements specified in `requirements.txt` installed,
e.g., by doing:

```
pip install -r requirements.txt
```

Then you will need to acquire a
[https://api.census.gov/data/key_signup.html](Census API key). Write this down
in a convenient place. (We use our password managers.) But also we suggest
creating a `.env` file that looks like `.env.sample` and put your API key
in the designated location.

You will then need to look up various geographic codes to find exactly what you
want. There are examples in line of how to do this!

## But what about....

This does *not* include everything. If you can't find a variable you would like
to grab, you can find [the full variable
list](https://api.census.gov/data/2017/acs/acs5/variables.html) on the Census's
website. There are a *lot* of them and it can be hard to parse through, so good
luck!

## General notes

The Census names variables in a seemingly inscrutible way. In general, however,
they satisfy the following regex: `[A-Z][0-9]{5}_[0-9]{3}[EM]A?`. The first letter tells you a general category of what the variable is about, e.g., `B` is generally demographic data.

The next 5 numbers simply the variable's serial number. The next three numbers
tend to break the variable down into cross tabs. For instance, `B01001` is the
`SEX BY AGE` variable, breaking down the population in a given geogrphy by sex
and age. `B01001_001` represents the *total* people in the area, whereas
`B01001_002` counts the total *male* population and `B01001_003` counts the
total male population under 10 years old.

Finally, the last 1 or 2 letters tells you what the number represents. `E`
represents the actual estimate. `M` represents the margin of error. An `A`
represents special annotations. For most work using big numbers, you can just
get away with looking at the `E` variable. However, for small numbers you
definitely want to look at the `M` variable and likely also the `A`s.

An example of a `big` number is the total population in a census tract
`B01001_001E`. However, a `small` number might be total number of male workers
who bike to work `B08006_031E`. 
