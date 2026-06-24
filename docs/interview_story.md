# Interview Story

## Situation

I wanted to build a data science project that was close to a real pricing and portfolio problem. Personalised registration plates are a good case because the value is not only numeric. Short plates, low numbers, repeated characters, names and cultural meaning can all change the price.

The main business question was simple: should every plate be sold in the same way, or should the portfolio be routed into different commercial paths?

## Approach

First, I audited the 2025 auction data and kept the modelling dataset focused on complete event-level records. I did not mix older historical data into training because those sources were partial and biased toward top sales.

I created explainable plate features, such as plate length, digit count, low-number indicators, repeated characters, format groups and structural rarity signals.

I used an event-based split instead of a random split:

- B270-B276 for training
- B277 for validation
- B278 for final testing

This was important because the model should work on a future auction event, not only on randomly mixed records from the same events.

I compared Ridge, Random Forest and HistGradientBoosting models. HistGradientBoosting had a slightly lower validation MAE, but the difference was very small. I selected Random Forest because it had a good balance of error, premium capture and explainability.

After the valuation model, I built a premium and collectible layer. This separated high market value from structural collectibility. Then I built a pricing and auction strategy simulation that routed assets into fixed price, standard auction, premium showcase or specialist review.

## Result

The final Random Forest model reached about GBP 1,248 MAE on the untouched B278 final test event, with about GBP 621 median absolute error. It captured about 55% of top-decile premium assets.

The decision layer routed 1,981 final-event assets into four paths:

- 1,482 Fixed Price
- 235 Standard Auction
- 54 Premium Auction / Showcase
- 210 Specialist Review

The routing groups were commercially distinct. Median observed prices increased from about GBP 1,010 in Fixed Price to about GBP 7,005 in Premium Auction / Showcase.

## Common Interview Questions

### Why did you choose this project?

I chose it because it combines valuation, feature engineering, premium asset detection, explainability and commercial decision-making. It is more realistic than only building a model score.

### What was the biggest data problem?

The biggest problem was data coverage. The 2025 DVLA data was strong and complete enough for modelling. Older sources were partial and selected, so I kept them separate.

### Why did you not use older years in the model?

Because they were not the same type of data. They mostly represented selected top sales or editorial reports. Mixing them with the full 2025 distribution would create sampling bias.

### Why did you avoid a random split?

A random split would mix auction events together and make the model look safer than it is. I used event-based validation so the model had to generalise to a later auction event.

### Why did you choose Random Forest?

HistGradientBoosting had a very small MAE advantage on validation, but Random Forest was easier to explain and had a good balance across premium capture, RMSE, median error and feature importance.

### Why are premium assets still hard?

Premium value often comes from meaning. A model using only structural plate features cannot fully understand names, words, brands, culture or collector demand.

### What is the difference between dynamic pricing and this simulation?

This project is a pricing and auction strategy simulation. It uses transparent policy assumptions and retrospective checks. A live dynamic pricing system would need conversion, demand, bidder, reserve-test and time-to-sale data.

### How would you take this to production with VicRoads internal data?

I would add listing impressions, enquiry data, bidder counts, bid sequences, customer segments, sell-through, time-to-sale and controlled pricing experiments. I would also track human overrides and monitor model drift.

### How would a commercial team use the result?

The team could use it to prioritise review work, identify premium or collectible assets, set indicative price ranges, route assets to the right sales path and decide where human judgement is needed.

