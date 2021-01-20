---
layout: post
title:  "GradCafe Data Analysis"
date:   2021-01-19
categories: grad-school gre gradcafe
hasmath:   "true"
---

GradCafe is a site that allows graduate school applicants to share their results and questions regarding their applications. The site acts like a forum for students to interact, but, perhaps more importantly, it also indirectly or directly gathers *a lot* of data.

Previous analysis have been done using GradCafe data. I am standing on the shoulders of these giants:

* [Debarghya Das's analysis](https://debarghyadas.com/writes/the-grad-school-statistics-we-never-had/)
* [Reddit post on timelines](https://www.reddit.com/r/gradadmissions/comments/7srxxy/decision_timelines_for_particular_universities/)

I will not be repeating those same analyses. However, some results might be confirmed by my own analysis. The main focus however of this post is to answer some commonly asked questions regarding graduate admissions, GRE scores, GPA, international vs national status, etc.

Plus, it's been 5 years since Debarghya's analysis, so this analysis is probably worth it if only just to double check if some conclusions still hold.

## Some Disclaimers

I wouldn't be able to sleep at night without adding some huge disclaimers to this post so here you go. The results and entries presented and analyzed here are probably the very definition of selection bias. Here are some possible issues with data:

* The overall population on the site is comprised of probably the more dedicated applicants
* Applicants are more likely to post their results if accepted
* Applicants with better stats are more likely to include them overall
* Applicants might feel pressured into padding their stats when reporting them
* Applicants with good stats but that got rejected are probably more likely to include their stats than rejects with not-so-great stats
* Applicants might take the GRE multiple times and include only their best score when submitting applications and reporting to GradCafe

## How I Obtained the Data

I scraped the data using code [available on GitHub](https://github.com/jjdelvalle/gradcafe_analysis) that's largely based on Debarghya Das's code. However, I adapted it for python 3 and added some usability extras so that anyone can download the data they feel they need and can stay up to date without relying on me or anyone to upload a new database of GradCafe entries. Additionally, I made it so the requests be made asynchronously and thus the scraping happens at a faster rate.

## Overall GradCafe Statistics

The basic stats:

![All institution stats for PhDs](/assets/All_institutions_phd.png)

## GRE Stats

ETS presents the following data for the GRE:

| Test | $$N$$ | $$\mu$$ | $$\sigma$$ |
|-------|--------|---------|------|
| Verbal reasoning | 1,640,350 | 150.37 | 8.49 |
| Quantitative reasoning | 1,643,587 | 153.39 | 9.35 |
| Analytical writing | 1,635,221 | 3.58 | 0.85 |

These numbers do not align with the GRE stats gathered from GradCafe. This suggegsts that the biases I pointed out earlier do apply. However, these are the people who you'll be competing with, if you're applying at top programs or applying for fellowships, or if you're applying for scholarships. These are the more relevant stats for the more serious applicants, i.e. you, you reading this post.

### GPA Stats

While we don't have good stats for GPA, a source like [USNews](https://www.usnews.com/education/best-colleges/articles/2019-01-28/what-a-good-college-gpa-is-and-why-it-matters) claims that 2.0 should be an absolute minimum GPA to maintain, and even though grade inflation has been a clear phenomenon in the US, it's quite staggering how the GPA distribution for GradCafe users is so top heavy.

## Questions to be Answered

### Do international students have significantly different stats?

### When should you expect a response?

### How much does GPA matter?

### How much do the GREs matter?

I will be updating this post with stats and answers to those questions.

I will also be adding most posts with more questions to be answered.

