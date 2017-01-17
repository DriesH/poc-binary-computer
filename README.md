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

Op het einde vindt je al de schema's terug die ik getekend heb van deze computer.

## Let's get started.

### Adding

Ik ben begonnen met de twee 4bit adder chips (74LS283) hun datasheets op te zoeken. Daarin heb ik gevonden hoe de chips werken, en hoe ik van twee 4bit adders één 8bit adder kon maken. Eigenlijk ben je op dit moment al bijna klaar als je dit weet. In theorie natuurlijk.

Elke chip heeft een carry over bit, dit kan je eigenlijk het beste uitleggen aan de hand van good ol' cijferen uit de lagere school.

***Carry over bit***

![carry-over-bit](https://github.com/DriesH/poc-binary-computer/blob/master/images/8bit-computer.jpg)


Om dus van twee 4 bit adders een 8 bit adder te maken, moet je 1 van de carry overs vast hangen aan de andere zijn carry in. Dit zorgt ervoor dat als je 1000 + 1000 doet, je 10000 kan krijgen.

We moeten natuurlijk ook nog onze bits ergens vandaan laten komen. Hiervoor gebruik ik 2 dipswitches die ik register A en B ga noemen.
Beide registers hangen aan een Octal buffer (74LS245n). Dit moet omdat als ik een bit HIGH maak deze wordt los gekoppeld van de GROUND en dan gaat zijn spanning beginnen floaten. Omdat de 74LS283 vrij kieskeurig is in zijn signalen gaat hij floating waarden als HIGH altijd LOW maken. Met een buffer er tussen worden floating signalen HIGH en werkt het perfect met de twee adders. Dit is iets dat ik heel lang op heb liggen sukkelen voor ik door had wat nu eigenlijk het probleem was.

### Subtracting

![me-building-it](https://github.com/DriesH/poc-binary-computer/blob/master/images/me-building-it.gif)
***Me building it***

Om binair van elkaar te kunnen aftrekken, moet je 1 van de registers zijn two's complement nemen. Dit doe je door eerst de bits allemaal te inverten en daarna de carry in bit van een van de twee adders die nog open is HIGH te maken. Wat je eigenlijk doet is, je inverteert het register en add een 1, wat je de two's complement geeft van de waarde in het register. Die 1 die je add is dan de teken bit. Tekenbit 1 is negetief, tekenbit 0 is positief.

Dus 0000 0011 - 0000 0001 geeft 0000 00010.

We kunnen ook negatief gaan:
Dus ***1*** 1111111 is -1 in decimaal. Enzovoort.


### Besluit

Je kan dus een 8 bit adder/subtracter maken, het enige nadeel is, binair lezen is verdomt moeilijk! :p

### Disclaimer

Ik heb voor het subtracten even hulp gevraagd aan mijn vader, vooral over de two's complement. Maar voor de rest heb ik alles aan de hand van mijn cursus digitale van 2 jaar geleden en het boek Digital Computer Electronics gemaakt.

### Schema's

![adding-two-registers](https://github.com/DriesH/poc-binary-computer/blob/master/images/8bit-computer_0001.jpg)
![inverting-a-register](https://github.com/DriesH/poc-binary-computer/blob/master/images/8bit-computer_0002.jpg)

### Bronnen

- Digital Computer Electronics
- Datasheets van alle chips
- Mijn vader (elektronica expert)
