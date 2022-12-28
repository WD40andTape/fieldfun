# *fieldfun*: Apply a function to the matching fields of structures

<!--[![View on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://mathworks.com/matlabcentral/fileexchange/)-->

## Summary

`S = fieldfun(fun,S1,...,SN)` passes the values for each field in structures `S1,...,SN` to function `fun` and returns the result in scalar structure `S`. Each field `F` in `S`, i.e. `S.(F)`, is the result of `fun(S1.(F),...,SN.(F))`.

[<img src="/diagram.png" width="700px">](https://mermaid.live/edit#pako:eNqtlV1vgjAUhv9K0yVkJiixu8OOq10OLualXZZCizQrxZSyxRj_-1pgTs1ETWgC_TiH0zcPPac7mFWMwxDmsvrOCqoNAK9vRAHb6iZda7opQEmFWhGI02gJnkEuuGR5ox7t4y-x9YrmOHBdP0P9bDab9StJtzLBQRoR-N6Fd40JzTMjKnXYtN14vgq67Y6ju489aRa10U1mvLVZ4EIHkXVrFZ27hgCL6IvKhuNARJ3V7-2eSuvN4viNUw3OYqErsdAdseIrseJLsQgMjnDV6AQMGgsMGhEMGhEMuhnM0wmYZCwwyYhgkhHBJLeCsTnaZa4d_OKwwzbnPgqqmOSOy0lS1geW9_JzVWEg7YA_cPT-Mx7wg8n9P-CSGDQkBg2JQXeJiW8REw-JiYfExJfF_B0Brlhfy-fAs-XDvZ7AdBo5QW1f93azlbwt9La-Sxk-5G2DPiy5tsvMXhE750qgKXjJCQztkFH9SSBRe-tHG1MttyqDoT0t3IfNhlHDXwS1d0gJw5zK2q5yJkyl4-7Oaa-e_Q8y9Axu)

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