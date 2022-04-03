# Kaggle - Spaceship Titanic

Entry for Kaggle competition - https://www.kaggle.com/competitions/spaceship-titanic/overview

## Intro

This is my second Kaggle competition. I'm trying to stop myself jumping in too deep so going through the learner competitions first. After this I will look at doing a few of the monthly competitions to see how they go.

## Initial thoughts

This seems fairly similar to the original titanic competition and will follow the same sort of methods I used in that.

## Data

- PassengerId - A unique Id for each passenger. Each Id takes the form gggg_pp where gggg indicates a group the passenger is travelling with and pp is their number within the group. People in a group are often family members, but not always.
- HomePlanet - The planet the passenger departed from, typically their planet of permanent residence.
- CryoSleep - Indicates whether the passenger elected to be put into suspended animation for the duration of the voyage. Passengers in cryosleep are confined to their cabins.
- Cabin - The cabin number where the passenger is staying. Takes the form deck/num/side, where side can be either P for Port or S for Starboard.
- Destination - The planet the passenger will be debarking to.
- Age - The age of the passenger.
- VIP - Whether the passenger has paid for special VIP service during the voyage.
- RoomService, FoodCourt, ShoppingMall, Spa, VRDeck - Amount the passenger has billed at each of the Spaceship Titanic's many luxury amenities.
- Name - The first and last names of the passenger.
- Transported - Whether the passenger was transported to another dimension. This is the target, the column you are trying to predict.

## Initial ideas

- Home planet could be one-hotted as a feature
- PassengerId
  - We could look at count of people in group
  - We could look at a 0/1 for travelling alone
  - Thoughts: When we're processing the test set for submission, can we combine the train and test to get this value? Because we will always know it, I don't *think* it's leakage.
- CryoSleep could be converted to 0/1
- Cabin could have deck and side extracted to one-hot features. Not sure if cabin number will be useful but we can investigate that
- Destination - Can one-hot this?
  - Possibly look at combinations of home planet and destination?
- Age - we could put this in to bins
- VIP - 0/1 for having paid or not
- Billing features
  - We could add these all together and bin them
  - We could look to see if there is specific location where spending money (or lots of it) helps predict
  - This could also be an indicator of someone who spends a lot of time outside their cabin?
- Name
  - We could look at a count of family members aboard
  - We could look at a 0/1 for travelling alone
  - Thought about male/female but the names are ambiguous