#### Short description
`vermouth-martinize` generates incorrect Martini 2.2 topologies for alpha-helical peptides. 

#### Detailed description
Using MODELLER, I generated a short 20 amino acids long polyleucine peptide in an alpha-helical conformation. I then used two different versions of `vermouth-martinize` (v0.9.6 and v0.9.7-dev9) and an old version of `martinize.py` script (labeled as version 2.6_3) to coarse-grain the peptide.

Commands used: 
- for `vermouth-martinize`: `-f l20.pdb -o topol.top -x l20_martini.pdb -ss HHHHHHHHHHHHHHHHHHHH -p backbone -ff martini22`,
- for `martinize.py`: `-f l20.pdb -o topol.top -x l20_martini.pdb -ss HHHHHHHHHHHHHHHHHHHH -p backbone`.

Both versions of `vermouth-martinize` generated identical topologies with the following `[ atoms ]` section:

```
[ atoms ]
 1 N0   1 LEU BB   1   1
 2 AC1  1 LEU SC1  2 0.0
 3 N0   2 LEU BB   3 0.0
 4 AC1  2 LEU SC1  4 0.0
 5 N0   3 LEU BB   5 0.0
 6 AC1  3 LEU SC1  6 0.0
 7 N0   4 LEU BB   7 0.0
 8 AC1  4 LEU SC1  8 0.0
 9 N0   5 LEU BB   9 0.0
10 AC1  5 LEU SC1 10 0.0
11 N0   6 LEU BB  11 0.0
12 AC1  6 LEU SC1 12 0.0
13 N0   7 LEU BB  13 0.0
14 AC1  7 LEU SC1 14 0.0
15 N0   8 LEU BB  15 0.0
16 AC1  8 LEU SC1 16 0.0
17 N0   9 LEU BB  17 0.0
18 AC1  9 LEU SC1 18 0.0
19 N0  10 LEU BB  19 0.0
20 AC1 10 LEU SC1 20 0.0
21 N0  11 LEU BB  21 0.0
22 AC1 11 LEU SC1 22 0.0
23 N0  12 LEU BB  23 0.0
24 AC1 12 LEU SC1 24 0.0
25 N0  13 LEU BB  25 0.0
26 AC1 13 LEU SC1 26 0.0
27 N0  14 LEU BB  27 0.0
28 AC1 14 LEU SC1 28 0.0
29 N0  15 LEU BB  29 0.0
30 AC1 15 LEU SC1 30 0.0
31 N0  16 LEU BB  31 0.0
32 AC1 16 LEU SC1 32 0.0
33 N0  17 LEU BB  33 0.0
34 AC1 17 LEU SC1 34 0.0
35 N0  18 LEU BB  35 0.0
36 AC1 18 LEU SC1 36 0.0
37 N0  19 LEU BB  37 0.0
38 AC1 19 LEU SC1 38 0.0
39 N0  20 LEU BB  39  -1
40 AC1 20 LEU SC1 40 0.0
```

`martinize.py` script generated this `[ atoms ]` section:

```
[ atoms ]
    1    Qd     1   LEU    BB     1  1.0000 ; 1
    2   AC1     1   LEU   SC1     2  0.0000 ; 1
    3    Nd     2   LEU    BB     3  0.0000 ; 1
    4   AC1     2   LEU   SC1     4  0.0000 ; 1
    5    Nd     3   LEU    BB     5  0.0000 ; 1
    6   AC1     3   LEU   SC1     6  0.0000 ; 1
    7    Nd     4   LEU    BB     7  0.0000 ; 1
    8   AC1     4   LEU   SC1     8  0.0000 ; 1
    9    N0     5   LEU    BB     9  0.0000 ; H
   10   AC1     5   LEU   SC1    10  0.0000 ; H
   11    N0     6   LEU    BB    11  0.0000 ; H
   12   AC1     6   LEU   SC1    12  0.0000 ; H
   13    N0     7   LEU    BB    13  0.0000 ; H
   14   AC1     7   LEU   SC1    14  0.0000 ; H
   15    N0     8   LEU    BB    15  0.0000 ; H
   16   AC1     8   LEU   SC1    16  0.0000 ; H
   17    N0     9   LEU    BB    17  0.0000 ; H
   18   AC1     9   LEU   SC1    18  0.0000 ; H
   19    N0    10   LEU    BB    19  0.0000 ; H
   20   AC1    10   LEU   SC1    20  0.0000 ; H
   21    N0    11   LEU    BB    21  0.0000 ; H
   22   AC1    11   LEU   SC1    22  0.0000 ; H
   23    N0    12   LEU    BB    23  0.0000 ; H
   24   AC1    12   LEU   SC1    24  0.0000 ; H
   25    N0    13   LEU    BB    25  0.0000 ; H
   26   AC1    13   LEU   SC1    26  0.0000 ; H
   27    N0    14   LEU    BB    27  0.0000 ; H
   28   AC1    14   LEU   SC1    28  0.0000 ; H
   29    N0    15   LEU    BB    29  0.0000 ; H
   30   AC1    15   LEU   SC1    30  0.0000 ; H
   31    N0    16   LEU    BB    31  0.0000 ; H
   32   AC1    16   LEU   SC1    32  0.0000 ; H
   33    Na    17   LEU    BB    33  0.0000 ; 2
   34   AC1    17   LEU   SC1    34  0.0000 ; 2
   35    Na    18   LEU    BB    35  0.0000 ; 2
   36   AC1    18   LEU   SC1    36  0.0000 ; 2
   37    Na    19   LEU    BB    37  0.0000 ; 2
   38   AC1    19   LEU   SC1    38  0.0000 ; 2
   39    Qa    20   LEU    BB    39 -1.0000 ; 2
   40   AC1    20   LEU   SC1    40  0.0000 ; 2
```

Clearly, the bead types for the backbone of the aminoacids near the termini of the peptide differ, with `martinize.py` generating correct bead types. Note especially that  `1 N0   1 LEU BB   1   1` which is a charged backbone bead obviously should not be of type `N0`.

The parameters for bonds, angles, position restraints, and dihedrals seem to be consistent between the individual scripts.

I have attempted to force `vermouth-martinize` to generate the correct topology by providing a slightly different secondary structure. Namely, I used `-ss 1111HHHHHHHHHHHH2222` instead of `-ss HHHHHHHHHHHHHHHHHHHH` but obtained the same (incorrect) result as before.

#### Files
All input and output files as well as the specific version of the `martinize.py` script used can be temporarily found at [github.com/Ladme/vermouth-martinize-bug](https://github.com/Ladme/vermouth-martinize-bug) until the issue is resolved.

#### Acknowledgemtns
Credit goes to Denys Biriukov and Peter Pajtinka for discovering this issue.