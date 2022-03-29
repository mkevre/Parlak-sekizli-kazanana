## References

A Git reference (`git ref`) is just a file that contains a Git commit SHA-1 hash.
When referring to a Git commit, you can use the Git reference, which is an
easy-to-remember name, rather than the hash. The Git reference can be rewritten
to point to a new commit. A branch is just a Git reference that stores the new Git
commit hash. These endpoints allow you to read and write [references](https://git-scm.com/book/en/v1/Git-Internals-Git-References)
to your Git database on {% data variables.product.product_name %}.