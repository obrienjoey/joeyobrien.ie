+++
title = "A generalization of the classical Kelly betting formula to the case of temporal correlation"
date = "2020-06-22"

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
publication_short = "IEEE Control Systems Letters"

# Abstract and optional shortened version.
abstract = "For sequential betting games, Kelly's theory, aimed at maximization of the logarithmic growth of one's account value, involves optimization of the so-called betting fraction $K$. In this paper, we extend the classical formulation to allow for temporal correlation among bets. For the example of successive coin flips with even-money payoff, used throughout the paper as an example demonstrating the potential for this new research direction, we formulate and solve a problem with *memory depth* $m$.  By this, we mean that the outcomes of coin flips are no longer assumed to be i.i.d. random variables. Instead, the probability of heads on flip $k$ depends on previous flips $k-1,k-2,...,k-m$. For the simplest case of $n$ flips, even-money payoffs and~$m = 1$, we obtain a closed form solution for the optimal betting fraction, denoted $K_n$, which generalizes the classical result for the memoryless case. That is, instead of fraction $K = 2p-1$ which pervades the literature for a coin with probability of heads $p \\ge 1/2$, our new fraction $K_n$ depends on both $n$ and the parameters associated with the temporal correlation model. Subsequently, we obtain a generalization of these results for cases when $m > 1$ and illustrate the use of the theory in the context of numerical simulations."

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
doi = "https://doi.org/10.1109/LCSYS.2020.3004029"
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
