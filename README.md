<h1 align="center">exec-tests</h1>
<p align="center"> Run tests from an executable.</p>

</br>

#### How to use it

1. Create the `__tests__` directory.
2. Write expected `in[X]` and `out[X]` files inside the tests directory.
3. Run the app using the executable: `./exec-tests --exe [EXECUTABLE]`

</br>

#### Installation

Download the app and run:

```bash
chmod +x ./exec-tests
```

</br>

#### Options

`--exe [EXECUTABLE]`: Set the executable file to be used.
</br>
`--continueInError`: Make the app continue working even with errors.
