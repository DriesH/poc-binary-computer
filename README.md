# Proof of Concept: Can you build an 8bit adding and subtracting ALU.

![header-img](https://github.com/DriesH/poc-binary-computer/blob/master/images/header-img.jpg)

## Index
- [What do you need?](https://github.com/DriesH/poc-binary-computer#what-do-you-need)
- [Let's get started](https://github.com/DriesH/poc-binary-computer#lets-get-started)
- [Bronnen](https://github.com/DriesH/poc-binary-computer#bronnen)


## What do you need?

![what-you-need](https://github.com/DriesH/poc-binary-computer/blob/master/images/composition-what-you-need.jpg)

Met deze componenten heb je genoeg om een heel basic 8bit adder te maken.

Als je wilt kunnen subtracten moet je 2 XOR chips (74LS86) hebben en een switch zodat je je computer in 2 standen kan zetten.

## Let's get started.

Ik ben begonnen met de twee 4bit adder chips (74LS283) hun datasheets op te zoeken. Daarin heb ik gevonden hoe de chips werken, en hoe ik van twee 4bit adders één 8bit adder kon maken. Eigenlijk ben je op dit moment al bijna klaar als je dit weet. In theorie natuurlijk.

Elke chip heeft een carry over bit, dit kan je eigenlijk het beste uitleggen aan de hand van good ol' cijferen uit de lagere school.

***Carry over bit***

![carry-over-bit](https://github.com/DriesH/poc-binary-computer/blob/master/images/carry-over-bit.jpg)


Om dus van twee 4 bit adders een 8 bit adder te maken, moet je 1 van de carry overs vast hangen aan de andere zijn carry in. Dit zorgt ervoor dat als je als je 1000 + 1000 doet, je 10000 kan krijgen.
