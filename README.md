# Test Git Partial Clone Big Small

Test repo for: https://stackoverflow.com/questions/600079/how-do-i-clone-a-subdirectory-only-of-a-git-repository/52269934#52269934

This repo is designed such that if you clone anything outside of `small/` or `small2/`, then you get at least 100 MB extra random data, so it will be very noticeable on the network/disk usage.

Contents:

* [big](big/): 10x random 10 MB files (~100 MB), small filenames
* big0-big9: 10x random 10 MB files (~100 MB). These were added to ensure that toplevel objects are not fetched.
* [big_tree](big_tree/): 10x directories with 50k empty files each, each with filenames of 200 random bytes long (~100 MB across 10 large tree objects). To ensure that unnecessary tree objects are not fetched.

  GitHub refuses the upload because the object is too large if we don't split the tree into 10 smaller ones.
* [small](small/): 1000x 1 B files, small filenames. The usual download target.
* [small2](small2/): 1000x 1 B files, small filenames. To see if the method supports downloading multiple directories at once together with `small`
