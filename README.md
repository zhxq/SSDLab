# SSDLab: Filling in the Missing Piece: Integrating Storage into CompOrg Courses

This repo contains source code template for `SSDLab` presented in the paper _Filling in the Missing Piece: Integrating Storage into CompOrg Courses_, published at ASEE 2025. Link to the paper will be updated after the paper is published.

## For Instructors

### Required Environments

System: Linux. Each student should be assigned to a folder under `/home/`.

Toolchain for the assignment: `gcc`, `objcopy`.

Handout: Any LaTeX compiler.

### Deployment

The assignment WILL NOT run properly without running actions below before assignment deployment. Please read this section before deploying the assignment. Instructors should send an email to xzhang84[at]syr.edu for access to instructors-only files to properly deploy the assignment. Please send proofs to prove that you are an instructor (e.g., sending your public profile on your institution website with the email address shown on your profile) for access. We apologize for any inconvenience, but we require this because the instructor-only files contain sample answers.

## Files for Students

Students should make changes to the following files:

- `handlewrite.c`: Students should make change to the `handleWriteRequests` function.
- `gc.c`: Students should make change to the `gc` function.
- `findvictim.c`: Students should make change to the `findVictim` function.

Students can use the autograder file (`autograder.py`) to grade their own assignments. Run `autograder.py` without any arguments for help.

All other files do not need to be changed by students or instructors.

- `helper.c`: Contains all helper functions. We strongly suggest students to read this file to learn how the helper functions are implemented. This file also helps students to learn C language syntax.
- `autograder.py`: Autograder for students.
- `waf.c`: Hooks on the students' implementation of the `gc` function to count the number of pages relocated in their garbage collection process.
- `main.c`: Trace driver. Reads in the trace and calls the `handleWriteRequests` for each write request in the trace.
- `Makefile`: Contains the instructions to `make` the assignment.
- `sample_findvictim.o`: The object file containing a sample answer of `findVictim` function for student debug purposes. Students can `make` with this sample `findVictim` function using `make withsamplefindvictim` before implementing their own version or to debug with it.
- `sample_gc.o`: Similar to above, but for the `gc` function. Run `make withsamplegc` to compile with `sample_gc.o`.
  - To compile with both `sample_findvictim.o` and `sample_gc.o`, run `make withsamplefindvictimandgc`.
  - The `autograder.py` script also provides the feature to compile with these object files.
- `ssdlab-ref`: The compiled `SSDLab` binary with sample answers to the three functions students need to solve. This is used by the autograder as reference.

## Acknowledgements

- The trace driver, `main.c`, is designed based on the structure of `csim.c` in CSAPP:3E. The handout is also based on CSAPP:3E assignment handout LaTeX template.
- The physical page address data structure, `ppa`, is based on the implementation of [FEMU](https://github.com/MoatLab/FEMU) by Huaicheng Li.
- The traces under the `./traces` folder are from the Systor 2017 paper _[Understanding Storage Traffic Characteristics on Enterprise Virtual Desktop Infrastructure](https://dl.acm.org/doi/10.1145/3078468.3078479)_. The traces are available at [http://iotta.snia.org/traces/block-io/4928](http://iotta.snia.org/traces/block-io/4928).
