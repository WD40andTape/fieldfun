# *fieldfun*: Apply a function to the matching fields of structures

<!--[![View on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://mathworks.com/matlabcentral/fileexchange/)-->

## Summary

`S = fieldfun(fun,S1,...,SN)` passes the values for each field in structures `S1,...,SN` to function `fun` and returns the result in scalar structure `S`. Each field `F` in `S`, i.e. `S.(F)`, is the result of `fun(S1.(F),...,SN.(F))`.

[<img src="/diagram.png" width="700px">](https://mermaid.live/edit#pako:eNqtlVFrgzAQx79KyKCsYCtN32zm0x6nD-tjM0Y0sQZiLDFulNLvvhhd126rrWBAk9wd55-fudwBpiXjMICZLD_TnGoDwMsrUcCOqk62mu5yUFChNgTiJFyDJ5AJLllWq0f7eGtso8IF9pup26FuN5_PO0vcWqbYT8KJSqrdqv9N4FsroRlMaJ4aUaqTMCdusfFbSecK3AekWVVG16mZbM0K59oPbZhT_Ts0AFiEH1TWHPsibL1e5_-rCica_MqFbuRCA3JFN3JF13IR6J_hqtAFGDQWGDQiGDQiGHQ3mOUFmHgsMPGIYOIRwcT3grF13Fa3XXzjsEtXc-85VUzyhstFUVYnlkP5NTdHT9kBr-fo_ec84QfT4T_gmhjUJwb1iUGDxET3iIn6xER9YqLrYn6OAFesu-8XYGKvj-a1BLNZ2Ahyc9X5zV5y1wxsD5AyeMjcgB4suLZmZtvIoQkl0OS84AQGdsl4RmtpCCTqaENpbcr1XqUwsAeGe7DeMWr4s6C21RQwyKisrJUzYUodta3JdajjFzZwGik)

`fieldfun` allows the organization of data by structure and field name while allowing the data to be easily processed according to the semantically meaninful fields, improving code readability. When only one structure is supplied, `fieldfun` can also be used as an alternative to `structfun`, the difference being that the output of `structfun` is an array, while `fieldfun` returns a structure, retaining the input format, again improving readability.

### Inputs

- `fun` is either a function handle or a text scalar giving the function's name or operator. The function must take N input arguments, i.e. equal to the number of input structures, and return a value. `fun` is called once for each field `F` in `S1,...,SN`.
- `S1` is a scalar structure or array of structures.
- `S2,...,SN` are scalar structures, arrays of structures, or variables of any other class. If `S2,...,SN` are structures, their fields and field order must match `S1`. If `S2,...,SN` are not structures, then they are converted to structures, with the value being assigned to each field.

### Output
- `S` is a scalar structure with the same fields and field order as `S1`. The value of each field `F` in `S`, i.e. `S.(F)`, is the result of `fun(S1.(F),...,SN.(F))`.

### Example
```MATLAB
treatmentGroup(1) = struct( 'name', "John", 'age', 30, 'vaccinated', true );
treatmentGroup(2) = struct( 'name', "Jane", 'age', 80, 'vaccinated', false );
controlGroup = struct( 'name', "Jim", 'age', 50, 'vaccinated', true );
allParticipants = fieldfun( @horzcat, treatmentGroup, controlGroup )
```
```
allParticipants = struct with fields:
        name: ["John"    "Jane"    "Jim"]
         age: [30 80 50]
  vaccinated: [1 0 1]
```
More examples available in [*examples.mlx*](examples.mlx) / [*examples.pdf*](examples.pdf).

## License and Citation
Published under MIT License (see [*LICENSE.txt*](/LICENSE.txt)). Please cite George Abrahams (https://github.com/WD40andTape/fieldfun).