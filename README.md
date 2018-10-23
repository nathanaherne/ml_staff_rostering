**Current Status of this repository** -> a work in progress

# Background

This is an issue that I have been working on and pondering for a long time. I have owned retail businesses for many years, know people who work at the upper levels of large retail organizations and worked as CTO in organizations that employ large number of staff. For this reason, staff rostering has been something I have thought about for a long time. It wasn't until a few weeks ago, when chatting to a friend, that I was reminded that staff rostering still wasn't an issue that had been solved effectively. I decided to see if using deep learning could help bridge the gap between current solutions and fully automated/digital staff rostering.

# Using this in your organization

Deep learning models sometimes need to be tweaked to suit a particular organization's data or business model. When discussing the data and creating the deep learning model, I will try to make it obvious as to how you could tweak the model to fit your particular use case. Alternatively, if you would like me to help tweak the model to fit your organization's requirements, please contact me.

# End goal

This document outlines the design of a software program which leverages the power of deep learning to automatically roster staff. I will be creating and documenting this algorithm in the context of a retail supermarket chain, though the ideas documented here could be easily transferred over to any other industry which needs to roster people.

The end goal of this algorithm will for the algorithm to roster staff automatically and have rostered staff levels reflect how many customers need to be served, while also considering:

1. The organizations legal responsibilities
	a. minimum time the staff can be rostered for in a single shift
	b. minimum skill sets required in the business
	c. number of staff per customer (if there is a legal requirement)
2. The number of staff required to run the organization based on its operating mode (open/stocking/closed etc)

The end goal of this algorithm is to:

1. increase the quality of customer service
2. reduce staff costs and therefore increase profitability

# Data Analysis

The data you feed a deep learning algorithm is extremely important because a deep learning algorithm learns from the data you feed it. If you do not understand the data, misinterpret what the data is telling you, feed the algorithm incorrect data or miss important correlations, the algorithm will not be particularly useful. This is the main reason why most deep learning experts spend 75% of their time on the data.

With this in mind, we will be considering the available data first and then move onto creating a deep learning model to help reduce loss prevention.

# Data Correlations

In some situations, you need multiple deep learning algorithms working together to create the required outcome. This problem is one that requires multiple algorithms because staff levels should follow customer service requirements. 

The models we will need to create are:

1. Sales prediction model
2. Staff rostering model

# Sales Prediction model

For a problem like rostering, sales prediction only needs to predict sales volumes for whatever time your organization plans out rostering. For example, if your organization sends rostering information out 4 weeks in advance, the sales model only needs to predict for 4/5 weeks ahead.

When creating and training a sales prediction model, it should be able to find the correlations between sales and the events that produced an increase or decrease in them. 

When predicting future sales, the model needs to be able to consider upcoming events when making its predictions. The further away from today, the less sure the model will be in regards to its sales predictions.

Things that the model would need to consider are:

1. Amount of staff working at the time - there is a correlation between sales and staff numbers.
2. Regulatory changes (plastic bag rules)
3. Weather patterns -> hot days means more drinks
4. The day of the week, holidays, pupil free days, government benefit payment days.
5. Natural disasters, both before and after they have occurred
6. Stock levels - low stock levels have a correlation to sales
7. Product prices - lower prices could result in more sales
8. Population around the store - to provide normalization of store sales
9. Competition and its effect in sales.
10. Marketing campaigns or press coverage

When creating a sales prediction model, we need to consider each store as a separate entity but also be aware that some events have not occurred to some stores (for example competition).

Each store has departments within it, who sales increase or decrease independently to the store as a whole.

The model will need to be able to connect to external prediction models (like weather) to use them in its training and prediction.

## Budgeting

Having a sales prediction model would be very useful for budgeting. A budgeting model could be created to receive the inputs of the sales prediction model and output running budget predictions throughout the year.

## New store locations

Having a sales prediction model would be very useful for deciding where new stores should be located. A store location model could be created to recommend new store locations and predict if existing stores are viable or what additions to the stores could increase their viability.

# Staff Rostering model

The staff rostering model will need to consider the following:

1. staff availability
2. staff skills and training
3. [staff availability score](#staff-availability-score)

## Staff Availability Score

The model will be able to create a availability score - staff that are regularly unavailable for their rostered time on will receive a lower score than those who are available more often. This will help the organization to work with the staff member to help them solve any issues that may be holding them back from being able to contribute in their chosen profession.


# Supporting software

Rostering staff is just part of the problem of rostering. Things change for staff members, events occur, sickness happens. One thing that significantly reduces the amount of staff required for managing those changes is software that allows staff to organise themselves.


