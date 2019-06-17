_Lambda School Data Science — Classification 2_ 

This sprint, your project is with Lending Club data, historical and current. Predict if peer-to-peer loans are charged off or fully paid. Decide which loans to invest in.

# Making datasets, Avoiding leakage

#### Objectives 
- join real-world data to make a new dataset
- remove features to avoid leakage
- begin with baselines: expected value of random decisions

#### [Data Science Is Not Taught At Universities - And Here Is Why](https://www.linkedin.com/pulse/data-science-taught-universities-here-why-maciej-wasiak/)

> The tables they use in machine learning research already have the target information clearly defined. Here comes the famous IRIS dataset, then the Wisconsin Breast Cancer, there is even Credit Risk or Telco Churn data and they all have the Target column there ...

> The problem is that in real life the Target flag is NEVER there.

> Your source will be a database with tens or hundreds of tables, millions of records, usually after 3 painful migrations with gaps in history, columns without descriptions ...

> Flooded by leaks from the future, ...a dozen of other traps ... And you need to disarm all of them, because even one left behind may result in a completely useless model. 

> These are the skills employers are looking for.

### Download data

- [Current loans](https://drive.google.com/uc?export=download&id=1OWH4bEzfKodNLkpNxxCr7qklCPPdlQsD) ([Source](https://www.lendingclub.com/browse/browse.action))
- [Data Dictionary & Historical loans](https://www.lendingclub.com/info/download-data.action) (17 zip files, 450 MB total)

### Background

[According to Wikipedia,](https://en.wikipedia.org/wiki/Lending_Club)

> Lending Club is the world's largest peer-to-peer lending platform. Lending Club enables borrowers to create unsecured personal loans between $1,000 and $40,000. The standard loan period is three years. Investors can search and browse the loan listings on Lending Club website and select loans that they want to invest in based on the information supplied about the borrower, amount of loan, loan grade, and loan purpose. Investors make money from interest. Lending Club makes money by charging borrowers an origination fee and investors a service fee.

[Lending Club says,](https://www.lendingclub.com/) "Our mission is to transform the banking system to make credit more affordable and investing more rewarding." You can view their [loan statistics and visualizations](https://www.lendingclub.com/info/demand-and-credit-profile.action).

Lending Club's [Investor Education Center](https://www.lendingclub.com/investing/investor-education) can help you grow your domain expertise. The article about [Benefits of diversification](https://www.lendingclub.com/investing/investor-education/benefits-of-diversification) explains,

> With the investment minimum of $1,000, you can get up to 40 Notes at $25 each.

![](https://i.ibb.co/B37q8LB/www-lendingclub-com-browse-browse-action-1.png)

### Use a subset of Loan Status

#### [Data-Driven Investment Strategies for Peer-to-Peer Lending: A Case Study for Teaching Data Science](https://www.liebertpub.com/doi/full/10.1089/big.2018.0092)

> Current refers to a loan that is still being reimbursed in a timely manner. Late corresponds to a loan on which a payment is between 16 and 120 days overdue. If the payment is delayed by more than 121 days, the loan is considered to be in Default. If LendingClub has decided that the loan will not be paid off, then it is given the status of Charged-Off.

> These dynamics imply that 5 months after the term of each loan has ended, every loan ends in one of two LendingClub states—fully paid or charged-off. We call these two statuses fully paid and defaulted, respectively, and we refer to a loan that has reached one of these statuses as expired.

> **One way to simplify the problem is to consider only loans that have expired at the time of analysis.**

> A significant portion (13.5%) of loans ended in Default status; depending on how much of the loan was paid back, these loans
might have resulted in a significant loss to investors who had invested in them. The remainder was Fully Paid—the borrower fully reimbursed the loan’s outstanding balance with interest, and the investor earned a positive return on his or her investment. Therefore, to avoid unsuccessful investments, our goal is to estimate which loans are more likely to default and which will yield low returns. 

### Use a subset of Loan Grade

[Lending Club announced,](https://blog.lendingclub.com/q1-2019-platform-update) 

> We periodically adjust platform products to reflect changes in investor demand and other marketplace factors. As a result, this quarter we are retiring Grade E loans. As of May 7, 2019, we will no longer facilitate new Grade E loans except for certain previously qualified or approved loans; **effective July 1, 2019, no grade E loans will be available on the platform.**

### Use a subset of features

What subset of features should we use, to avoid leakage?

### More notebooks
- https://github.com/h2oai/h2o-tutorials/tree/master/best-practices/feature-engineering
- https://github.com/oracle/Skater/blob/master/examples/credit_analysis/Credit_Analysis.ipynb