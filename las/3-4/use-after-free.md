(Describe the practical ramifications of computational undecidability.)

Recall from CSC 161 that a _use-after-free_ error arises in C whenever we:

+   Obtain a pointer to a chunk of memory allocated via `malloc`.
+   Free that chunk of memory with `free`.
+   Attempt to access the chunk of memory after it has been freed through the pointer.

For example, here is a function that exhibits a use-after-free error depending on its input:

~~~c
void sometimes_bad(int n) {
    int *px = (int*) malloc(sizeof(char) * 10);
    for (int i = 0; i < 10; i++) { px[i] = i; }
    if (n > 0) {
        free(px);
    }
    printf("%d\n", px[5]);    // use-after-free error if n > 0
}
~~~

Tools like Valgrind and AddressSanitizer instrument our C code so that these kinds of errors can be detected at runtime on specific inputs. But, of course, it would be much nicer to detect these errors at compilation time for any C program and any input.

In a few sentences, describe why undecidability theory tells us that such an analysis at compilation time will necessarily be incomplete.

(_Hint_: Consider applying the spirit of Rice's Theorem to this situation.)

|___|
