This document outlines the design of a machine learning algorithm to roster staff. It is said that 75% of the time spent designing an algorithm is used considering the data you have available, what insights it provides and then creating a robust machine learning algorithm that will work with the data.


# The end goal
The end goal of this algorithm will for the algorithm to roster staff automatically and have rostered staff levels reflect how many customers need to be served, while also considering:

1. The organizations legal responsibilities
	a. minimum time the staff can be rostered for in a single shift
	b. minimum skill sets required in the business
	c. number of staff per customer (if there is a legal requirement)
2. The number of staff required to run the organization based on its operating mode (open/stocking/closed etc)

The end goal of this algorithm is to:

1. increase the quality of customer service
2. reduce staff costs and therefore increase profitability

# Analogy

If you have read any of my previous discussions around developing machine learning models, I like to use analogies to illustrate what the data means in a "real world" context. **I will be using the analogy of a retail supermarket chain**

# Data required

There is always a balancing act between the amount of data easily available and the amount of data required to create a good machine learning model. One of the great things about Machine Learning models is that they often shed much more information than expected. For just a little more data, the organization gets many new insights into their business.

In some situations, you need multiple machine learning algorithms working together to create the required outcome. This problem is one that requires multiple algorithms because staff levels should follow customer service requirements. 

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


