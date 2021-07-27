\name{randomForestTest}
\alias{randomForestTest}
%- Also NEED an '\alias' for EACH other topic documented here.
\title{
Random Forest Test
}
\description{
Random Forest Test (RFtest) is a multivariate global test based on random forests for high-dimensional and phylogenetically related microbiome data. It is a permutation test using generalization errors as an effect size. It is robust to outliers and powerful for phylogenetically clustered signals. It automatically detects interactions and non-linear associations without prior knowledge and data transformation.
}
\usage{
randomForestTest(comm, meta.data, response.var, status.var = NULL, adjust.vars = NULL,
                 prediction.type = c('Classification', 'Regression', 'Survival'),
                 method = c('weighted','omnibus','unweighted'), tree = NULL,
                 probability = TRUE,presence.in = 2,  test.type = c('OOB', 'Training',
                 '0.632', '0.632+'), perm.no = 999, pearson.fit = FALSE,trace = FALSE,
                 n.cores=detectCores()-1, reps = 3, ...)
}
%- maybe also 'usage' for other objects documented here.
\arguments{
  \item{comm}{Microbial community data with samples arranged in rows and OTU/ASV in columns.}
  \item{meta.data}{Meta data for the microbial community data with samples arranged in rows and response and confounding variables in columns.}
  \item{response.var}{Character. The name of the response variable in the meta.data}
  \item{adjust.vars}{Character. The name(s) of the covariates in the meta.data}
  \item{prediction.type}{Character. It should be one of 'Classification', 'Regression' or 'Survival'. Partial match is allowed. Classification for binary response variable and Regression for continuous response variable.}
  \item{method}{Character. The name(s) of the covariates in the meta.data}
  \item{tree}{A phylogenetic tree. If not given, the random forest test will run in a non-phylogenetic verison.}
  \item{probability}{If error rates are predicted with probability for a binary response variable.}
  \item{presence.in}{A number. OTUs/ASVs should be present in at least this number. If presence.in < 1, it would specify the proportion of OTUs/ASVs.}
  \item{test.type}{Character. It should be one of 'OOB', 'Training', '0.632' or '0.632+'. Partial match is allowed.}
  \item{perm.no}{Numeric. The number of permutations.}
  \item{pearson.fit}{Should predict with pearson fit? Default FALSE.}
  \item{trace}{Should this function be traced. Default FALSE.}
  \item{n.cores}{Numeric. Number of cores used.}
  \item{reps}{Integer. Reptitions used to calculate and stabilize stat.o.}
  \item{...}{Other arguments used in ranger}
}
\details{
%%  ~~ If necessary, more details than the description above ~~
}
\value{
%%  ~Describe the value returned
%%  If it is a LIST, use
%%  \item{comp1 }{Description of 'comp1'}
%%  \item{comp2 }{Description of 'comp2'}
%% ...
}
\references{
%% ~put references to the literature/web site here ~
}
\author{
Lujun Zhang, Jun Chen
}
\note{
%%  ~~further notes~~
}

%% ~Make other sections like Warning with \section{Warning }{....} ~

\seealso{
%% ~~objects to See Also as \code{\link{help}}, ~~~
}
\examples{
  library(GUniFrac)
  library(ranger)
  library(ape)
  library(vegan)
  library(parallel)

  data("throat.otu.tab")
  data("throat.meta")
  data("throat.tree")

  x <- throat.otu.tab
  x <- x / rowSums(x) #normalization, relative abundance
  tree <- throat.tree
  x<-x[,tree$tip.label]

  pv1 <- randomForestTest(comm = x , meta.data = throat.meta,  tree=tree,
                          response.var="SmokingStatus",
                          perm.no = 999, test.type = "OOB", method = "w")
  pv1$p.value.perm #0.001

}
% Add one or more standard keywords, see file 'KEYWORDS' in the
% R documentation directory (show via RShowDoc("KEYWORDS")):
% \keyword{ ~kwd1 }
% \keyword{ ~kwd2 }
% Use only one keyword per line.
% For non-standard keywords, use \concept instead of \keyword:
% \concept{ ~cpt1 }
% \concept{ ~cpt2 }
% Use only one concept per line.
