# Lab Report: Week 5

### Researching `grep`

All of the following options were found in the GNU `grep` manual page at [https://www.gnu.org/software/grep/manual/grep.html](https://www.gnu.org/software/grep/manual/grep.html). Their respective sections where further details can be found have been written down (e.g. 2.1.6).

1. `-r` (2.1.6) Takes directory(ies) as input instead of file(s). Reads all files in the given directory and its subdirectories, recursively.
    1. *Input.*

        ```bash
        grep "greetings" -r ./written_2/
        ```

        *Output.*
        ```
        ./written_2/travel_guides/berlitz2/Bahamas-Intro.txt:To make the most of your trip you’ll need to tune your mind to “Bahamian time.” On New Providence and Grand Bahama this may not be much slower than at home, but on the Out Islands, time definitely runs more slowly, and nothing is so important that it can’t wait a while. People are more important than to-do lists, so a leisurely exchange of greetings and an inquiry about your family’s well-being precedes any business activity. This genuine thoughtfulness also extends to visitors; someone will always go out of their way to be helpful, in ways that have been lost in more developed locations.
        ./written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt:A pretty little village of pastel-colored clapboard houses, Hope Town is full of friendly locals. Kids run safely in the streets of the traffic-free town center and along the Queens Highway, only slightly wider than a sidewalk. Shoes are optional in the bars at the water’s edge, and as the sun sets you’ll hear a thousand stories here about the one that got away. Watch out for the sign “Tourists treated just like locals,” for you’ll soon feel as though you’ve lived here forever. You’ll be exchanging greetings, and before you know it, life stories. The Wyannie Malone Historical Museum on Queens Highway is the place to find out more about these fascinating people and their home island.
        ```

        *Explanation.* The `grep` command searches for matches of the phrase "greetings" in every file in `./written_2/`, including subdirectories, which is why it finds text files in `./written_2/travel_guides/berlitz2/`. This is useful because the wildcard `<dir>/*.txt` only lists files in the `<dir>` directory, excluding subdirectories.

    1. *Input.*

        ```bash
        grep "tasty" -rl ./written_2/
        ```

        *Output.*
        ```
        ./written_2/travel_guides/berlitz2/Berlin-WhereToGo.txt
        ./written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
        ./written_2/travel_guides/berlitz2/CanaryIslands-History.txt
        ./written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt
        ./written_2/travel_guides/berlitz2/Bermuda-WhatToDo.txt
        ./written_2/travel_guides/berlitz2/China-WhereToGo.txt
        ./written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt
        ./written_2/travel_guides/berlitz1/WhatToEdinburgh.txt
        ./written_2/travel_guides/berlitz1/HandRIsrael.txt
        ./written_2/travel_guides/berlitz1/WhatToIstanbul.txt
        ./written_2/travel_guides/berlitz1/WhereToLosAngeles.txt
        ./written_2/travel_guides/berlitz1/WhereToJapan.txt
        ./written_2/non-fiction/OUP/Berk/CH4.txt
        ./written_2/non-fiction/OUP/Rybczynski/ch1.txt
        ```

        *Explanation.* Here we combine the `-r` option with the `-l` option (which we learned in lab), which only shows the names of files with matches. The `grep` command now lists all files in `./written_2/` that contain the phrase "tasty", including subdirectories, which is why it finds files in several different subdirectories, despite only supplying the parent directory. Again, this is useful because without the `-r` option, we'd have to pass the files as arguments individually (e.g. `./written_2/travel_guides/berlitz2/*.txt ./written_2/travel_guides/berlitz1/*.txt ...` etc.).

1. `-L` (2.1.3) Displays which files do *not* contain any matches.
    1. *Input.*

        ```bash
        grep "where" -L ./written_2/non-fiction/OUP/Castro/*.txt
        ```

        *Output.*
        ```
        ./written_2/non-fiction/OUP/Castro/chW.txt
        ./written_2/non-fiction/OUP/Castro/chY.txt
        ```

        *Explanation.* The `grep` command lists all text files in the directory `./written_2/non-fiction/OUP/Castro/` which do *not* contain the phrase "where", which leaves only `chW.txt` and `chY.txt`. This exclusive behavior is extremely useful. For example, if we have a bunch of submitted coursework with their respective submitter's name at the top of each file, we could use the `-L` option to exclude all files that contain a person's name, so that the only files that are listed are those that *don't* contain their name.
    
    1. *Input.*

        ```bash
        grep "sea" -rL ./written_2/
        ```

        *Output.*
        ```
        written_2/travel_guides/berlitz2/Budapest-History.txt
        written_2/travel_guides/berlitz2/Barcelona-History.txt
        written_2/travel_guides/berlitz2/Amsterdam-Intro.txt
        written_2/travel_guides/berlitz1/HandRLasVegas.txt
        written_2/travel_guides/berlitz1/HandRIstanbul.txt
        written_2/travel_guides/berlitz1/WhatToIndia.txt
        written_2/travel_guides/berlitz1/HistoryLakeDistrict.txt
        written_2/travel_guides/berlitz1/HistoryHongKong.txt
        written_2/travel_guides/berlitz1/HistoryEdinburgh.txt
        written_2/travel_guides/berlitz1/WhatToFrance.txt
        written_2/travel_guides/berlitz1/HistoryIsrael.txt
        written_2/travel_guides/berlitz1/HistoryIstanbul.txt
        written_2/travel_guides/berlitz1/HandRIbiza.txt
        written_2/travel_guides/berlitz1/HistoryJerusalem.txt
        written_2/travel_guides/berlitz1/IntroJerusalem.txt
        written_2/travel_guides/berlitz1/HandRMadrid.txt
        written_2/travel_guides/berlitz1/IntroIndia.txt
        written_2/travel_guides/berlitz1/HistoryEgypt.txt
        written_2/non-fiction/OUP/Kauffman/ch7.txt
        written_2/non-fiction/OUP/Castro/chZ.txt
        written_2/non-fiction/OUP/Fletcher/ch10.txt
        ```

        *Explanation.* This time, we combine the `-L` option with the `-r` option, which was covered in the previous section. Now, the `grep` command lists all files in the `./written_2/` directory (and all subdirectories, recursively) that do *not* contain the phrase "sea". Maybe this is useful if we really hate the ocean (though "sea" matches more than just the word "sea", such as "**sea**son").

1. `-n` (2.1.4) Displays line numbers of matches.
    1. *Input.*

        ```bash
        grep "Lucayans" -n ./written_2/travel_guides/berlitz2/*.txt
        ```

        *Output.*
        ```
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt:6:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt:7:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
        ```

        *Explanation.* The `grep` command shows the line numbers "6" and "7". This is useful for quickly locating where the matches occur (since normally, it only displays the line itself).

    1. *Input.*

        ```bash
        grep "sauce" -rn ./written_2/
        ```

        *Output.*
        ```
        ./written_2/travel_guides/berlitz2/Berlin-WhereToGo.txt:181:The museum documents the achievements of the most progressive 20th-century European school of architecture and design. Architects Walter Gropius, Mies Van der Rohe, and Marcel Breuer, along with artists Paul Klee, Vasili Kandinsky, Lyonel Feininger, Oskar Schlemmer, and Laszlo Moholy-Nagy attempted to integrate arts, crafts, and architecture into mass industrial society. On view here is a selection of the objects they created: tubular steel chairs, cups and saucers, teapots, desks, new weaves for carpets, chess pieces, and children’s building blocks, as well as some pioneering architectural plans and sketches.
        ./written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt:37:Puerto Rican folk music is rich with songs based on real-life issues faced by the jíbaros, the ordinary country folk of the island — death, unrequited love, and poverty resulting from bad harvests. Salsa is probably the most famous form of music to emerge from Puerto Rico. Ironically, salsa (which means “sauce”) was imported back to the island from the Puerto Rican community who settled in New York city in the late 1940s. Salsa combines an array of percussion instruments with a swinging horn section. You will hear it everywhere. A much older “Latin” dance making a comeback is the merengue, which, when it first became popular, was considered to be so provocative that it was banned by the Spanish authorities.
        ./written_2/travel_guides/berlitz2/NewOrleans-History.txt:7:The Native Americans (Choctaws and other tribes) who settled here thousands of years before the arrival of the French colonists lived a simple life. Although they needed to avoid water snakes, alligators, and disease-carrying mosquitoes, they enjoyed a cornucopia of seafood and game, flavoring it with a hot sauce the Creoles would later adopt. They used the waterways of the Mississippi delta as highways, navigating their dugout canoes through the impenetrable and ever-changing maze of bayous.
        ./written_2/travel_guides/berlitz2/China-WhereToGo.txt:107:Sichuan cuisine, one of the four great schools of Chinese cooking, produces such imaginative creations as “abalone and chrysanthemums,” “peonies and butterflies,” and “stewed bear’s trotters in brown sauce.” One of the most famous dishes, mapo dofu, consists of beancurd infused with chili peppers in a manner that numbs the tongue upon impact.
        ./written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt:59:Business is centered on La Rampa, the name for Calle 23 from Calle L to the sea. Opposite the tower-block Hotel Habana Libre — the Havana Hilton in pre-revolutionary days — is the Coppelia ice cream park. At this institution, locals queue for hours for the prized ice cream, eating several scoops in one sitting or ladling them into saucepans to take home. Hard-hearted foreigners paying in dollars down their scoops in a cordoned-off area. Coppelia was instrumental in the award-winning Cuban film Fresa y Chocolate (“Strawberry and Chocolate”), a daring film about freedoms and revolutionary fervor in contemporary Havana (its title is a wry reference to the lack of choices of ice cream flavors — indeed, of all things — in Cuba).
        ./written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:87:The seafood and fish of the Mediterranean provide some of the coast’s most memorable meals. A great favourite is zarzuela de mariscos, a variation of a Catalan dish, which combines many different ingredients, just like the Spanish operetta from which it takes its name. Shellfish is served with rice in an unlikely but very tasty sauce of olive oil, ground almonds, assorted spices, and chocolate, though local cooks sometimes cheat a bit by adding octopus and other shell-less tidbits.
        ./written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:88:Then there is langosta — spiny lobster — as succulent and as expensive as ever, and sometimes priced per 100 grammes (be sure to read the menu’s small print to make sure). Gambas are prawns, and langostinos the jumbo-sized version. Try them a la plancha (grilled), a la romana (fried in batter), or al pil pil in a hot spicy sauce. Emperador (swordfish) is especially good grilled, and lenguado (sole) is delicious in batter, grilled, or sautéed in butter. For something different, try dorada a la sal: a whole fish is packed in wet salt, then baked. It comes to the table in a shiny white jacket that is broken when the fish is cut and served.
        ./written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:93:Alioli, a whipped sauce of fresh garlic and olive oil, accompanies many dishes. It’s a piquant speciality of the region, and an excellent one.
        ./written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:97:A tapa is a mouthful of anything that tastes good and fits on a cocktail stick. The variety is enormous: smoked mountain ham, spicy sausages, cheese, olives (some as big as pigeon’s eggs), sardines, mushrooms, mussels, squid, octopus, meatballs, fried fish, plus sauces and exotic-looking specialities of the house. The name comes from the practice, sadly almost vanished, of providing a free bite with every drink. The tidbit was put on a small plate traditionally used to cover the glass and came to be called a tapa, which means lid.
        ./written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:100:The Spaniards start the day with bread, a simple roll, or the traditional churro, a kind of elongated fritter made by pouring a batter-like mixture into a cauldron of hot olive oil. The golden-brown result is dusted with sugar, sometimes coated with chocolate sauce, or both.
        ./written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:150:chuletachopssalsasauce
        ./written_2/travel_guides/berlitz1/WhereToMallorca.txt:802:        a beautiful rock basin like sauces bubbling in a pan. The “pools” are
        ./written_2/travel_guides/berlitz1/IntroFrance.txt:34:        soufflé or a rich hollandaise sauce that makes an egg proud to be an
        ./written_2/travel_guides/berlitz1/WhatToIstanbul.txt:297:        kuru fasulye (haricot beans in tomato sauce), patlıcan kizartması
        ./written_2/travel_guides/berlitz1/WhatToIstanbul.txt:303:        fillet cooked in a sauce flavoured with ground walnuts and paprika.
        ./written_2/travel_guides/berlitz1/WhatToIstanbul.txt:325:        served on a bed of diced pide bread with tomato sauce and yoghurt,
        ./written_2/travel_guides/berlitz1/WhatToIstanbul.txt:328:        served with a tomato sauce, are called köfte. A classic Turkish dish,
        ./written_2/travel_guides/berlitz1/HistoryIbiza.txt:58:        moneymaker in an exotic, aromatic sauce of decomposed fish innards.
        ./written_2/travel_guides/berlitz1/WhatToIbiza.txt:491:        drink, the food being served on a saucer sitting on top of the glass
        ./written_2/travel_guides/berlitz1/WhereToFWI.txt:774:        featuring delicate wine sauces, and gendarmes (if only a mere handful).
        ```

        *Explanation.* Again, we combine the `-n` option with the `-r` option to search all files in the `./written_2/` directory (and its subdirectories, recursively). This time, we see all matches for the phrase "sauce" along with their line numbers. This could be useful if we really want to know about all the different sauces in all these countries but also want to do some further reading (in which case the line numbers tell us where to look).

1. `-C x` (2.1.5) Displays **x** lines of context before and after matches.
    1. *Input.*

        ```bash
        grep "sauce" -C 5 ./written_2/travel_guides/berlitz1/IntroFrance.txt
        ```

        *Output.*
        ```
        their clothes and perfumes, their dashing art and monumental
        architecture. Their love of perfection serves them well.
        Give French cooks a couple of eggs and they won’t just boil
        them, fry them, or make an omelette (all of which they’re quite
        prepared to do superlatively) — they feel obliged to produce a delicate
        soufflé or a rich hollandaise sauce that makes an egg proud to be an
        egg. Even a lowly croque-monsieur is a world away from a ham and cheese
        sandwich. You will still find the elegant, spare plates of ­nouvelle
        cuisine, but there is a new focus on heartier dishes and an acceptance
        of cuisines of other countries.
        The French attention to detail is found in all walks of life
        ```

        *Explanation.* The `grep` command displays the matched line (in the middle) plus 10 lines of context (5 before and 5 after). This makes the output a lot more readable/understandable for humans, since the matched line is often not a complete sentence. Looking at the output above, we can actually understand the context for why the word "sauce" comes up and can actually read some interesting information.

    1. *Input.*

        ```bash
        grep "Lucayans" -C 3 -rn ./written_2/
        ```

        *Output.*
        ```
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt-3-
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt-4-
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt-5-A Brief History
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt:6:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt:7:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt-8-English sea captains also came to know the beautiful but deserted Bahamian islands during the 17th century. England’s first formal move was on 30 October 1629, when Charles I granted the Bahamas and a chunk of the American south to his Attorney General, Sir Robert Health. But nothing came of that, nor of a rival French move in 1633 when Cardinal Richelieu, the 17th-century French statesman, tried claiming the islands for France.
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt-9-Colonization and Piracy
        ./written_2/travel_guides/berlitz2/Bahamas-History.txt-10-In 1648 a group of English Puritans from Bermuda, led by William Sayle, sailed to Bahamian waters and established the first permanent European settlement on the island they named Eleutheria (now Eleuthera) after the Greek word for freedom. The 70 colonists called themselves the Eleutherian Adventurers, but life was very difficult and the colony never flourished, though Sayle was long honored for the effort. In 1666 a smaller island (called Sayle’s island) with a fine harbor was settled by Bermudians and renamed New Providence. It was later to become known as Nassau, capital of the Bahamas.
        ```

        *Explanation.* This time, we combine the `-C 3` option with the `-rn` options, which we covered in the previous section (recursive search with line numbers). Now `grep` shows both where the matches occur and the surrounding 3 lines of context. The matched lines have their line numbers surrounded by `:` (e.g. lines 6–7), while the context lines have their line numbers surrounded by `-` (e.g. lines 3–5, 8–10). The line numbers make differentiating between context/match lines a little easier, so the `-C x` and `-n` options work well together.
