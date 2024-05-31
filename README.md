## Table of contents
#### Who is this for
#### Read this before your interview day
#### RTL Design
#### Topics covered
#### Some “gotchas”
#### Some challenging interview questions
#### Resources



#### Design Verification
- Topics covered
- Some “gotchas”
- Some challenging interview questions
- Resources

#### Architecture / Performance modeling
- Topics covered
- Some “gotchas”
- Some challenging interview questions
- Resources

#### Some company specific insights



Just a disclaimer - like every other interview preparation resource, this is not exhaustive. Use
this as a guide, but try to come up with customized plans for yourself.

## Who is this for

Anyone looking for internships or entry level positions in Hardware Engineering. A lot of this was
written off our experiences looking for summer internships and jobs during BS/MS, but this can
be extended to other cases too.

## Read this before your interview day

From personal experience and after talking about this to many others, it is clear that interviews
are less about how much you have prepared and more about how well you do on the given day.
There is so much randomness that no amount of preparation can guarantee success. This
section was not in the original draft, but I am adding it because I wish someone had told me this
earlier.

At this moment, your upcoming interview might feel like the most important thing in your life. But
nothing can be further from the truth. Just think back at everything that you thought were big
moments - some exams, presentations, etc. Most of them have probably vanished from your
memory. This interview would be no different. The worst thing that will happen is that you will not
get this role. And that would make no difference after a few weeks when you are giving other
interviews (and you will get more opportunities!). So don't let the results affect you. All you can
do is control the controllables - answer every question you know the answer to in the best way
you can, and hope for the best.


## RTL Design

Involves the design/integration of digital logic modules that go into a chip or IP.

### Topics covered

- Verilog syntax and programming
    - Try to be familiar with all the synthesizable constructs used in Verilog
       - Ex. Blocking vs Non-blocking statements - trivial, but it is surprising how
          often it comes up (and how often interviewees stumble)
       - Casex, Casez and the variations
    - A very common question pattern:
       - Write Verilog code to do “something” (Ex. BCD counter)
       - What do the different sections of your code synthesize to - very important
          to know this, this is where Verilog interviews are different from other
          coding interviews. For example, always @ (posedge clock) would
          typically result in a logic involving Flip-Flops
       - Make some kind of changes to the input/output (Ex. Output should be
          triggered by another signal, Output should be seen with a delay of one
          cycle, Synchronous vs Asynchronous reset, etc)
- Digital Design concepts
    - Basic logic design (the kind of questions that show up in an undergraduate digital
       electronics course) - Ex. Universal gates, design different gates using a MUX
    - Designing a counter is also a commonly asked question
    - State Machine design
       - Design state machines (Draw the state diagram) for the given scenario
       - Mealy vs Moore model - very very important - learn how to come up with
          both models any scenario
       - Typically, state machine questions are converted to Verilog questions (i.e.
          write verilog code for the state machine you designed). It is good to
          practice a template for state machines (both models) so that you can
          convert any state diagram to code easily.
       - Another variation here could be binary encoding vs one-hot encoding for
          the states - each has pros and cons
- Static Timing Analysis
    - What the different terms (setup time, hold time, etc) mean
    - Given a Flop - Logic - Flop configuration
       - Is there setup or hold violations
       - If there are any, how to fix them
       - There are multiple variations of this question, and they are well
          documented in any STA book or tutorial - spend time to master this
    - Time borrowing (Especially if you are a grad student)
    - Metastability and how to deal with it


- Know the basics for all interviews, but also learn about specifics like
    MTBF in case of clocking-related roles
- C Programming
- Basic C programming could be asked in both RTL design and verification roles.
One should be able to code at least up to the complexity of Linked Lists.
- Sorting is also commonly asked

### Some “gotchas”

- Although you might be interviewing for an RTL design role, it is better to prepare a little
    above and below the VLSI stack
       - Up the stack: Computer Architecture - A theoretical understanding is
          recommended (The typical 5-stage pipeline, Memory hierarchy, Branch
          prediction, etc)
       - Down the stack: MOSFETs and CMOS design (These are not asked as often, but
          as a digital designer you are expected to know about CMOS inverters and basic
          logic gates at the transistor level)
- If you have previous experience in RTL design
    - Identify some key blocks from your previous design (Ex. Content Addressable
       Memories, FIFOs, etc) - this is a typical question to know how deep you have
       been
    - You should also be able to come up with a quick implementation of these
       structures (You could always skip the edge cases that would have been covered
       in the actual design, but be able to write basic working HDL)
    - Understand basic Valid-Ready handshaking and learn how to design for it. This is
       used in almost every digital block in the industry.
          - Read about the AXI protocols (the different channels and how
             transactions work) if you have any experience involving AXI blocks (which
             would be the case for most RTL in the industry)
                - “Backpressure” is something that is asked often - in simple words,
                   how do you tell the block before you that it needs to stop sending
                   data. The simple way to do this is using the valid-ready protocol,
                   but there are others (valid-afull, valid-credit, etc)
- If you are applying for an FPGA company or team, make sure you understand FPGAs
    well, and how they are different from ASICs
       - And also how to write better RTL for FPGAs (they are register rich, have hard
          DSP blocks, etc - how does this impact your design decisions?)

### Some challenging interview questions

- Minimum FIFO Depth Calculation given sender and receiver transfer rates (This can get
    complex with multiple inputs/outputs)
- FSMs
    - Serial 2’s complementer
    - Detect more than two 1’s in the last 3 samples
    - Pattern (Ex. 1011) detector - overlapping and non-overlapping case
- Verilog
    - Detecting positive edge/negative edge/both
    - FIFO (Usually for experienced candidates)
    - Clock dividers (Divide by 2, 3, etc) with different duty cycle
- CMOS
    - Which is faster - PMOS or NMOS? Why do we size them differently?
- Puzzles
    - Sometimes the interviewers end the round with some puzzle questions. One
such example question is - There are 25 horses with 5 race tracks. Each track
can be used to race 5 horses. You don't have a watch. Find the minimum number
of races needed to identify the top 3 fastest horses?

### Resources

Verilog basics practice (“leetcode for Verilog”) -https://hdlbits.01xz.net/wiki/Main_Page

Free verilog/system verilog simulation tool -https://www.edaplayground.com/- You can write
your own designs and testbenches for practice here

Some good coding guidelines -RTL_coding_guidelines

Good resource for FIFO depth calculation questions -
https://hardwaregeeksblog.files.wordpress.com/2016/12/fifodepthcalculationmadeeasy2.pdf

Low power RTL methods (Good to know for follow-up questions about improving your code) -
https://www.design-reuse.com/articles/20775/hdl-design-low-power.html

Common digital blocks in Verilog -https://verificationguide.com/verilog-examples/

Common digital blocks in System Verilog (Synthesizable) -
https://www.asic-world.com/examples/systemverilog/index.html

Cracking the Digital VLSI Verification Interview (Book by Ramdas Mozhikunnath and Robin
Garg) - This is a great book for basic digital design questions. Can skip the verification part for
RTL design roles.

FPGA specific concepts - this is a good playlist -
https://www.youtube.com/playlist?list=PLPmSCnkkX4qtfS4quvY2UDsNSBY5cuIB

Verilog Syntax Questions -http://asic.co.in/Index_files/verilog_interview_questions.htm

Designing an Arbiter -https://github.com/bmartini/verilog-arbiter


Designing FIFOs the right way -
[http://www.sunburst-design.com/papers/CummingsSNUG2002SJ_FIFO1.pdf](http://www.sunburst-design.com/papers/CummingsSNUG2002SJ_FIFO1.pdf)

In general all Sunburst papers are very good if you want to become a better RTL designer (but
might be overkill just for an interview) -http://sunburst-design.com/papers/

Digital Logic RTL and Verilog Interview Questions (Book by Trey Johnson) - Excellent for RTL
interviews, has some challenging design questions

Some challenging FSM Questions -
https://www.vlsiuniverse.com/fsm-finite-state-machine-qustions/#:~:text=Design%20a%20finite
%20state%20machine%20%28FSM%29%20that%20will,and%20111.%20Let%20us%20assum
e%20four%20different%20states

A painstakingly long question list (worth skimming through, there are few interesting questions )

- https://cdcnitw.files.wordpress.com/2013/04/vlsi_questions.pdf

The typical STA interview question -
https://www.youtube.com/watch?v=iqvZLAgoA-g&list=PLD5C0Wv5Dnmdv-B6NGOu4MA3yDlqF
fdre&index=4&t=2s&ab_channel=ElectroTuts

https://www.youtube.com/watch?v=R50lGuibylE&list=PLD5C0Wv5Dnmdv-B6NGOu4MA3yDlqFf
dre&index=5&ab_channel=ElectroTuts

AXI protocol basics -
https://www.youtube.com/watch?v=1zw1HBsjDH8&list=PLaSdxhHqai2_7WZIhCszu5PLSbZUR
mibN&ab_channel=DillonHuff


## Design Verification

Involves writing tests for digital logic modules to cover all the different use-cases.

### Topics covered

- Digital Design concepts (Same as in RTL Design)
- C Programming (Same as in RTL Design)
- Scripting
    - Be very familiar with one scripting language
       - Industry uses a lot of TCL and Perl, but Python works well for entry level
          interviews
    - Questions usually involve large text files
       - So read about how to parse information from text files, and maybe some
          efficient ways to do it
- Object Oriented Programming (OOP)
    - Since a lot of System Verilog constructs are OOP based, understanding all the
       OOP concepts is important
          - Sometimes this is completely skipped, but good to know anyway
    - Be able to come up with code examples for each of the OOP principles (like
       Classes, Objects, Abstraction, Encapsulation, etc)
    - Inheritance and Polymorphism are usually favorites (Finding out which class
       different objects belong to)

### Some “gotchas”

- DV interviews are usually challenging because you are expected to also be a good
    designer. So I suggest preparing all the content of RTL design too.
       - Verilog design questions might be asked (Although they tend to be simpler)
- If you have previous DV experience (even in an internship), then you also need to work
    on UVM and other DV concepts that you might have used
       - In this case, the RTL Design part will probably be skipped

### Some challenging interview questions

Programming/Scripting:

- Given a log file with a set of Names and IDs, and another log file with IDs and Statuses,
    generate a log file with Names and Statuses. (The log files are large, so the script should
    be efficient)
- Write a program to remove duplicates from an array


### Resources

Basics of Verification with SystemVerilog -
https://www.youtube.com/channel/UCpO2gS_MinWY5Ii0HQ-nIpw

Assertions in SystemVerilog -
https://www.youtube.com/watch?v=OWW9pbFJPJU&list=PL7q7nkSfmotsyJxfvQFMyUvjKzOTS
47aN&index=4&ab_channel=SystemverilogAcademy

SystemVerilog OOP interview questions -
https://www.youtube.com/playlist?list=PLScWdLzHpkAcNa1vjkzPY7L1YiLbH0p

UVM Hello World Code -
https://www.youtube.com/watch?v=Qn6SvG-Kya0&ab_channel=EDAPlayground

Coding UVM components -https://verificationguide.com/uvm/uvm-testbench-architecture/

Cracking the Digital VLSI Verification Interview (Book by Ramdas Mozhikunnath and Robin
Garg) - Pretty comprehensive for DV roles

Quick Python tutorial to revise basic syntax -
https://www.youtube.com/watch?v=KPuA3Vq4yvY&ab_channel=365DataScience

Complete TCL syntax -
https://www.youtube.com/watch?v=6s6YbIa2k_g&ab_channel=MahendraMaramWorld

Free TCL compiler -https://www.jdoodle.com/execute-tcl-online/


## Architecture / Performance modeling

Working with Memory, Processors, IO and everything that defines how computers “compute”

### Topics covered

- There will almost always be questions on Caches
    - Basics - why do we need caches in the first place (memory hierarchy pyramid)
    - 3C’s of Cache - Compulsory, Capacity and Conflict misses + Coherence misses
       for multicore
    - Sizing and properties of caches at various levels
    - Cache coherence and the different coherence protocols
       - Should be able to walk through an example for each protocol
       - Why ‘O’ state in MOESI, why ‘E’ state in MESI?
    - Banking schemes in Caches - not many undergrad courses cover this, so needs
       extra preparation
    - Inclusiveness and exclusiveness of caches
    - Basic cache replacement policies (LRU, FIFO, SRRIP and other protocols if
       mentioned in resume projects).
          - Know for which workloads which works best (cache friendly workloads,
             scan based workloads, thrashing workloads and mixed workloads)
          - Coherence vs Consistency (Basic understanding of memory consistency
             is necessary)
- Pipeline basics
    - Hazards, Superscalar, etc
    - Different types of hazards and what exists in an in order pipeline
    - Hazards that arise in a pipeline with multiple functional units with different
       latencies (The issue is still in order to the Func. units, but they complete out of
       order)
    - Hazards in a full out of order pipeline and how to mitigate them
- Out of order execution
    - Should be able to walk through Tomasulo’s algorithm
    - Graduate students could be asked advanced concepts
       - Handling exceptions in Out of Order processors (precise exceptions)
       - Need of Reorder buffer, reservation station
       - RAT (register alias table)
       - Register renaming and different ways to achieve that (separate rename
          register file, physical register file concept, renaming using ROB, using the
          reservation station entries etc)
       - Think about when rename registers can be recycled/resued exactly?
       - Load Store Dependence (Memory disambiguation , load store
          forwarding,load store queue)
- Branch Prediction


- Different schemes (Gshare, Gselect, Bimodal, global vs local schemes)
- BTB (branch target buffer), Return address stack
- Value prediction and Prefetching (Usually not asked unless you might have specific
projects)
- Virtual memory
- Address translation mechanism in x86 using multi level page table, TLB
- Page table walk on a TLB miss
- VIPT (virtually indexed physically tagged) /PIPT caches
- Homonyms and Synonyms problems in the above caches and how to solve
them.
- Interrupts
- Basics on what they are, interrupts vs exceptions and how they are handled
- Basics OS theory-
- Threads, processes
- What happens on a process context switch vs thread context switch
- Mutex, Semaphore
- Internal implementation of mutex using (TestandSet, Compare and Swap,
load linked, store conditional. These are basically instructions in an ISA)
- Atomics
- Memory barriers and Memory fence
- Programming
- Typical C++ knowledge based questions - Classes, OOP concepts, etc
- Linked list manipulation - very important (Ex- Reversing linked lists, intersection
of 2 linked lists etc)
- Stacks and Queues (implementation from scratch)
- Bit manipulation questions - frequently asked
- Arrays (Two pointer techniques)
- Hash maps/ unordered maps (Mainly used in other problems due ot O(1) search
complexity)

### Some “gotchas”

- Since computer architecture comes under “computer science” in many places, there is
    an assumption that you are a good programmer
       - So if you are from an Electrical Engineering background, this could be the harder
          part of the interview. Spend a lot of time programming, and be familiar with
          language specific constructs (especially C++).
- In architecture interviews there is sometime more importance given to syntax than
    algorithms (Pseudo codes expected mainly atleast for many interviews)
-
- In general the “architecture” part of comp arch interviews are more of a discussion to
    know how much you are aware of. The questions will depend on how you answer. They
    might for example ask you to explain what all you know regarding the fetch stage. Say
    you start talking about icache. They might ask you for ideal sizing, associativity etc for


```
the icache. If you bring up I-TLB, then VM concepts come into picture. You might talk
about branch prediction in the first stage. Then they go deep about how BP is exactly
done.. Using BTB, BP-predictor (counter based), return address stack etc
```
### Some challenging interview questions

Programming

- Difference between shallow and deep copy - this is subtle, but important
- How do you find if 2 nodes in a graph are connected

Micro architecture

- In a typical MIPS ISA, you have only 2 working registers. But you have a large number of
    ALU units. Design an instruction to emulate swap

### Resources

For architecture good resources include -

```
● Gatech HPCA(Covers most concepts asked in interviews.Very short videos and easy to
follow. If you are still not exposed to comp arch and have interviews coming up, this is
the best place to get started in my opinion. It will take a few days to finish)
● madhu mutyam iit-m nptel (especially for out of orderexecution, superscalar
microarchitecture, coherence, synchronization concepts, memory consistency concepts)
● Onur Mutlu(Slightly long lectures, but gives a detailedunderstanding of the concepts)
● Modern processor design (Superscalar)(Chapters 4and 5 are very detailed for
superscalar microarch and arch for apple interviews (full time). This level might not be
expected during internships )
● Eric rotenberg slides
```
**Say you say I don’t know any DSA** , and need to havea good understanding of the basics.
This is possibly one of the best introduction to abstract data structures, array,linked lists, stack,
queue, trees, graphs. (9 hr video. Solid content. (dsa) <RIP Harsha/ HumbleFool >

**Say you don’t know even basics of pointers**. Anothergem of a video from humblefool
(pointers)

The best book on OS. Not super important, but good to know (OSTEP)

Some good set of programming questions (topic wise)- It is good to solve the first few questions
in all topics, though this comprehensive list is meant for software interviews (450 questions luv
bubbar)

Some basic C questions -https://www.interviewbit.com/c-interview-questions/


C/C++ knowledge based questions -
https://www.codingninjas.com/blog/2021/09/13/top-c-c-interview-questions-in-2021-part-1/

https://www.codingninjas.com/blog/2021/09/14/top-c-c-interview-questions-in-2021-part-2/

Basic C++ programs to understand syntax -
https://www.codezclub.com/cpp-solved-programs-problems-solutions/

This is a good (good=small here) set of programs for DSA questions (May not need this level for
Hardware interviews, but good to do anyway) -https://www.byte-by-byte.com/50-questions/

Low power design concepts for Power Architecture roles (Can clear many power arch roles if
these basics from NPTEL are known).

https://www.youtube.com/watch?v=TFOO1JAll2Y&ab_channel=VLSIPhysicalDesign

https://www.youtube.com/watch?v=ORtlxpW_LMU&ab_channel=VLSIPhysicalDesign

Quick recap for Cache Coherence protocols -
https://www.youtube.com/watch?v=r_ZE1XVT8Ao&ab_channel=NesoAcademy


## Some company specific insights

- Amazon has “leadership questions” in every interview
    - More info:
       https://www.scarletink.com/interviewing-at-amazon-leadership-principles/
    - Suggested preparation - write down one incident/story for each of the different
       situations - so you won’t have to think on the spot. This helped a lot.
          - Some categories I used were: Risk/Failures, Conflict at Work, Leading a
             project, Criticism, Project behind schedule, Choosing between
             technologies, Prioritizing Long term goals, etc
    - Even if this is just behavioral, it is better to be prepared even if it is not valued
       highly, because this is usually the first question, and messing it up could spoil
       your whole interview.
- Startup usually have more extensive interviews
    - Your previous experience is valued a lot - you are probably being interviewed for
       a very specific skill from your resume, so make sure you refresh on all your
       previous projects
    - Be able to demonstrate your previous projects in a quick way - For example,
       some wrapper code, skeleton blocks, etc.
- Traditional software companies (Ex. FAANG) that are building hardware still have a
    software engineering mindset - which is also reflected in the interviews
       - Interviews are programming centric
       - “Algorithmic thinking” and “Efficiency” are valued a lot
- Apple typically has a lot of rounds
    - But they typically get through them quickly after the phone screening round


## Other useful resources

- https://discord.gg/kaQpGzgN- A discord channel todiscuss Hardware Engineering
    interviews, offers, etc. Has lots of resources.


## Found this useful? Please fill out this survey as

## a “thank you”

# Hardware Engineering Interview Survey

The goal of this survey is to understand the challenges faced by anyone preparing for Hardware
Engineering interviews. Our aim is to make the process more streamlined, and this is the first
step towards achieving that. **All we need in returnis a minute of your time.**


