# Cheat Engine - Tutorial Series

Learned about CE as a kid, failed at doing the tutorial series abysmally. Decided to try it out again...

## Step Reference Table

| Steps         | Password    |
| -----------   | ----------- |
| Step 2        | 090453      |
| Step 3        | 419482      |
| Step 4        | 890124      |
| Step 5        | 888899      |
| Step 6        | 098712      |
| Step 7        | 013370      |
| Step 8        | 525927      |
| Step 9        | 31337157    |

## 32-bit and 64-bit gotchas

### Registers

eax, ebx, ecx and so on are actually **registers**, which can be seen as *"hardware"* variables, meaning different than higher level-language's variables. Registers can be used in your software directly with instructions such as `mov`, `add` or `cmp`. The leading `e` means extended that is your register is 32 bits wide. On the other hand, 64-bits registers begin by `r`.

These registers are not all used the same purposes as illustrated below. This graphic show the register usage for Linux 64-bit [ABI](https://en.wikipedia.org/wiki/Application_binary_interface).

<img src="https://res.cloudinary.com/wemakeart/image/upload/v1659295915/github/ce-tutorial/register-usage-linux-x64_b06x7k.png" width=650px height="740px"  alt="docs-icon"/>

All registers are not described in this capture though. For instance `*ip` is a special register ([process counter](https://en.wikipedia.org/wiki/Program_counter)) that holds the next instruction to bo executed.

You can find the [full ABI there](https://software.intel.com/sites/default/files/article/402129/mpx-linux64-abi.pdf). Some information is specific to Linux but most remains relevant for any [POSIX](https://en.wikipedia.org/wiki/POSIX)-compliant system.

### Step 9

1. **32-bit** - The x64 code injection technique does not work and throws a float exception. I instead found the pointers for Group 1's health values then set the value to 1 million and froze the value. This worked and the next button became clickable.
2. **64-bit** - The code injection technique works here. Find the health value of Dave, find what writes to the address, on the instruction - `Find out what addresses this instruction accesses` then compare the structures and find the unique values for each team and it's offset. Create a script comparing the values of the team-id and jump the instruction for group-1 that decreases the health. See folder - Step 9

<div align="center">
<img src="https://res.cloudinary.com/wemakeart/image/upload/v1659297100/github/ce-tutorial/gg-emoji_cicc9t.png" width=200px height="300px"  alt="docs-icon"/>
</div>

