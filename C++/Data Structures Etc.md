# Data Structures Etc.: Structs, Typedefs, Enums, and Aliases

## Struct

The **`struct`** keyword specifies a *structure*. A structure is a composite data type inherited from C. All members of a `struct` are public.

```cpp
struct TEMPERTURES {
    float high;
    float low;
    float average;
};
```

Additionally, you can create an instance of a `struct` using the optional declarator:

```cpp
struct TEMPERTURES {
    float high;
    float low;
    float average;
} dailyTemperatures, recordTemperatures;
```

The values in a `struct` are acccessed using the `.` operator:

```cpp
struct TEMPERTURES {
    float high;
    float low;
    float average;
} dailyTemperatures, recordTemperatures;

dailyTemperatures.high = 20.2;
dailyTemperatures.low = 14.4;
dailyTemperatures.average = 18.5;

recordTemperatures.high = 36.5;
recordTemperatures.low = -22.4;
```

## Typedefs
