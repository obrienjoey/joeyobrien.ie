+++
title = "A Generalization of the Classical Kelly Betting Formula to the Case of Temporal Correlation"
date = "2020-03-05"

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.

authors = ["**Joseph D O'Brien**", "Kevin Burke", "Mark E Burke", "B. Ross Barmish"]

# Publication type.
# Legend:
# 0 = Uncategorized
# 1 = Conference proceedings
# 2 = Journal
# 3 = Work in progress
# 4 = Technical report
# 5 = Book
# 6 = Book chapter
publication_types = ["2"]

# Publication name and optional abbreviated version.
publication = "IEEE Control Systems Letters"
publication_short = "IEEE-CSL"

# Abstract and optional shortened version.
abstract = "For sequential betting games, Kelly's theory, aimed at maximization of the logarithmic growth of one's account value, involves optimization of the so-called betting fraction $K$. In this Letter, we extend the classical formulation to allow for temporal correlation among bets. To demonstrate the potential of this new paradigm, for simplicity of exposition, we mainly address the case of a coin-flipping game with even-money payoff. To this end, we solve a problem with  _memory depth_ $m$.  By this, we mean that the outcomes of coin flips are no longer assumed to be i.i.d. random variables. Instead, the probability of heads on flip $k$ depends on previous flips $k-1,k-2,...,k-m$. For the simplest case of $n$ flips, with $m = 1$, we obtain a closed form solution $K_n$ for the optimal betting fraction. This generalizes the classical result for the memoryless case. That is, instead of fraction $K^* = 2p-1$ which pervades the literature for a coin with probability of heads $p \\geq 1/2$, our new fraction $K_n$ depends on both $n$ and the parameters associated with the temporal correlation. Generalizations of these results for $m > 1$ and numerical simulations are also included. Finally, we indicate how the theory extends to time-varying feedback and alternative payoff distributions."

# Featured image thumbnail (optional)
image_preview = ''

# Is this a selected publication? (true/false)
selected = true

featured = true


# Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter the filename (excluding '.md') of your project file in `content/project/`.
#projects = ["example-external-project"]

# Links (optional).
url_pdf = "https://arxiv.org/pdf/2003.02743.pdf"
url_preprint = "https://arxiv.org/abs/2003.02743"
url_code = ""
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""

# Custom links (optional).
#   Uncomment line below to enable. For multiple links, use the form `[{...}, {...}, {...}]`.
#[[url_custom]]
#name = "Journal"
#url = "https://link.springer.com/article/10.1007/s10584-014-1174-4"

# Does the content use math formatting?
math = true

# Does the content use source code highlighting?
highlight = true
  
# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
#[header]
# image = "memory_v7.jpg"
# caption = "My caption :smile:"

+++
