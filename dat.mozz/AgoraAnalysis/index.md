
_student work in R for the class [Foundations of Data Science](https://www.springboard.com/workshops/data-science)_

- [What/Why](#what-why)
- [R](#R)
- [Agora and Anonymous Markeplaces](#agora-and-anonymous-marketplaces)
- [the Data](#the-data)

to do:
- [What's in the data?](#whats-in-the-data)
- [How much drugs?](#how-much-drugs)
- [Poisson Regression Model] - on [GitHub](https://github.com/mozzarellaV8/agora-marketplace/blob/master/poisson.md) for now. 
- [Why (again)]
- make the `code` font smaller

.

![](http://pi.mozzarella.website/img/index-2015-07-07.jpg)

<a name="what-why"/>
# What / Why
</a>

This is an ongoing document for me to share and process thoughts on a darknet/anonymous market analysis project I'm working on. Yes yes, the Silk Roads, Agoras and Evolutions.

One reason this exists is to help bridge my interest in statistical computing to my other interests in art, photography, &c. Another reason is so I can consider the project in a context outside of GitHub/class. 

That said - the code and WIP are [here on GitHub](https://github.com/mozzarellaV8/agora-marketplace). 

I'll try to keep things communicable but there's a chance this document devolves into an info dump. 

<a name="R"/>
# R
</a>
...is a programming language specializing in statistical computing and graphics. When I first looked at the [website](htp://r-project.org) it seemed pretty intense. 

Some cool things you can do with R: 

- [extract/scrape data](http://stat4701.github.io/edav/2015/04/02/rvest_tutorial/) from websites, 
- explore and visualize large and/or complex datasets, 
- very easily fit statistical models to such datasets 
- (choosing, interpreting, and drawing meaningful conclusions from these models is another thing though) 

**_09-09-2016_** - recent cool example of an analysis done with R: [identifying Donald Trump's actual tweets vs. ones by his staff](http://varianceexplained.org/r/trump-tweets/), using sentiment analysis on the different tweet sources from his account (Android, iPhone). 

<a name = "agora-and-anonymous-marketplaces">
# Agora and Anonymous Marketplaces
</a>
market lifespan: _~2013 - 2015_

Agora was a referral-based darknet market, that rose to prominence after the demise of Silk Road 2 in 2014.

Given a small handful of other options, Agora was chosen as a market to analyze because of it's immense popularity, healthy usage rate, and scale. Additionally, the conditions of Agora's shutdown were unique to me in that the admins voluntarily shut it down after a [paper was published in August 2015](https://www.usenix.org/system/files/conference/usenixsecurity15/sec15-paper-kwon.pdf) that exposed vulnerabilities that could de-anonymize Tor users. 

This is in contrast to other markets of similar scale. Prominent shutdown examples are Silk Road's demise at the hands of law enforcement (twice); darknet markets [Evolution](https://www.deepdotweb.com/2015/03/18/evolution-marketplace-exit-scam-biggest-exist-scam-ever/) and [Sheep](https://www.deepdotweb.com/2013/11/30/sheep-marketplace-scammed-over-40000000-in-the-biggets-darknet-scam-ever/) turning out to be massive exit-scams.

It's a stretch to say (and impossible to prove) that Agora's administrators were completely altruisitic in their voluntary shutdown; but such protections of themselves and their clients might suggest that conducting business professionally was a priority above others. The circumstances seem novel for a world known more for multiple degrees of [deceptions](http://arstechnica.com/tech-policy/2016/08/stealing-bitcoins-with-badges-how-silk-roads-dirty-cops-got-caught/). 

<a name = "the-data">
# the Data
</a>

The data was acquired via crawls conducted by independent researcher Gwern: [black market archives](http://www.gwern.net/Black-market%20archives#grams). While there are some caveats to how representative these crawls are to actual darknet activity as a whole - it's still really fucking impressive.

So comprising this archive are weekly crawls of multiple anonymous marketplaces on the darknet - well-trafficked and documented sites such as **_Silk Road_**, **_Evolution_**, and **_Agora_** in addition to smaller, more ephemeral markets.

For Agora specifically, the crawl dates begin on _2014-01-01_ and end on _2015-07-07_. There are 206 daily crawls total - generally occurring weekly, but sometimes more frequently. The relevant directories ended up being `p` and `vendor` - individual product listing and vendor pages.

By my count so far: **_~2.47 million pages_** in `p` and **_~20k_** pages in `vendor`. 

![](http://pi.mozzarella.website/img/index-2014-01-01.jpg)

<a name = "whats-in-the-data">
# What's in the data?
</a>

or - "here's some information"

Extracting the data from the 2.47 million raw html files has been fun. It still is fun. Subsetting and deriving new features has been fun too. By 'fun', I mean 'fun' but also 'complicated to the point of confusion'. Decisions seem to only make sense after a week or month. Hindsight has been a good editor. Looking forward to when hindsight tells me why I spent so long pulling out every brand name in the `Counterfeits` category with regular expressions. OK!

![](http://pi.mozzarella.website/img/900x575-a1c2-01.svg)


Plotting the broad market `categories` by their `subcategories` and origin `location`. Gonna need to fix the font size on this plot for web. But from what I can see on the 11x17 printout in front me are a few questions: 

1. **1. What happens globally?**
	* Drugs (and mostly Drugs)
	* Counterfeits
	* Data/Info
	* Guides/eBooks

By a pretty large margin, `Drugs` is the most popular category worldwide, with `Cannabis` as the most popular subcategory. Cannabis also ends up having the most sub-subcategories - more on that later. Only one location - `Lithuania` - does not have **_any_ ** Drugs listings at all. (note: check a Lithuania subset for number of listings. I bet it'll be a lone vendor, listing one item for a couple weeks - just enough to appear on the table). 

`Singapore` almost had no drugs too, but `Prescriptions` make an appearance. It turns out `Scandinavia` lists just one: `Ecstasy`. 

2. **2. Who does it all?**
	* USA
	* UK
	* Australia
	* No Info
	* Torland
	* Worldwide

Of course only the top 3 listed are identifiable territories. I take 'does it all' as the locations covering the most categories and subcategories on offer. If `No Info` were an actual, singular place, it'd cover everything category the market offers except `Grinders`, `Paper`, and `Stashes` - cannabis accessories most people could buy at a local smoke shop. 

The only things that don't show up in the `USA` are `Clothing` and `Electronics` (Counterfeits) - funny enough, two areas `China` really lights up. `UK` also has little interest in dealing Counterfeits, but unlike the US there's a reasonable gun law in place there so trafficking in `Lethal Firearms` is not showing up.

3. **3. Niches**
	* Afghanistan
	* Aland Islands
	* Albania
	* Armenia
	* Bulgaria
	* Christmas Island
	* Columbia
	* Guatemala
	* Lithuania
	* Netherlands Antilles
	* Norway
	* Phillipines
	* Portugal
	* Scandinavia
	* Singapore
	* Ukraine
	* Zambia

I take niches to mean locations that offer listings in only one cat/subcat. When I find the better word I'll replace it. 

There's some geographic clusters that arise just from reading over the list - Scandinavia, Eastern Europe, Central/South America ('connected' by `Netherlands Antilles`), Southeast Asia (including `Christmas Island` - even though it's technically an Australian territory, it's geographically closer to Jakarta).  

`Portugal`-`Morocco` make a pair. `Afghanistan` and `Zambia` are out on their own, A-Z.

Gonna venture that internet connectivity plays a large role in whether a location has a robust darknet presence. 

Not sure that I trust the World Bank, but taking a look at their [Internet users per 100](http://data.worldbank.org/indicator/IT.NET.USER.P2) data might be a start for cross-comparison. Looks like it's just the annual proportion per 100 people of population total, weighted by aggregated average. This might be more helpful with each country's total population? Or relative percentage of internet users per each country's population? Nice, there's different metadata for almost every single data point...showing overall, a very uneven survey. Maybe another source for this information would be better. 

4. **4. What do most locations have in common?**
	* Cannabis
	* Ecstasy
	* Opioids
	* Prescription
	* Psychedelics
	* Stimulants

Essentially - every major class of Drug.

<a name = "how-much-drugs">
# How much drugs?
</a>

Exactly how much do Drugs comprise the total listings on Agora? Some quick calculations.

SVG Test:
![](http://pi.mozzarella.website/img/900x575-a1c2-01.svg)

.jpeg Test:
![](http://pi.mozzarella.website/img/1200px-a1c2-print-06.jpg)


Well, let's look at this image again until I go tinker with the php file to make it disappear:













