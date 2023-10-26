# Disclaimer

**The purpose of this repository is to provide clear instructions and guidelines for Daml learners to pass the Daml Fundamentals certification via their capstone project. Please bear in mind that any code within is provided for illustrative purposes only, and as such may not be production quality and/or may not fit your use-cases. You may use the contents of this repository in parts or in whole according to the BSD0 license:**

---

# 🛠️ Fast Food Restaurant 🛠️ 
This is an application to order food at a fast food restaurant built in Daml.

### I. Overview 
This project was created by using the `empty-skeleton` template. 

There are 2 parties, the customer and the restaurant. The customer and restaurant can interact with each other to order and serve fast food. The restaruant can choose to accept or reject orders. The customer can also choose between dining modes, items and discounts they want to apply. 


### II. Workflow
  1. Customer creates an Order contract
  2. Customer exercises StartOrder if they want to start ordering at the restaurant.
  3. Restaurant exercises StartOrder if they want to take an order from the customer.
  4. Customer exercises AddItems with a list of MealItem : (item, amount) they want to order. The items that exist with a valid amount are added.
  5. Customer exercises ApplyDiscounts with a code. The discount is applied if a valid code with the key exists. 
  6. Customer exercises PayOrder with an amount. Rejected if not enough money, accepted if enough. 
  7. Restaurant exercises ServeOrder. 
  8. Customer exercises PickUp order. Error if restaurant has not served it, fine otherwise. 

### III. Challenge(s)
* The project was created by using `empty-skeleton` and the following was removed from `daml.yaml`:
```
sandbox-options:
   - --wall-clock-time
```
and the following was added:

```
exposed-modules:
  - Main
```
For more info, check out [this post](https://discuss.daml.com/t/sandbox-options-wall-clock-time/5692/16?u=cathy_jung) on Daml Forum and [Daml Doc](https://docs.daml.com/tools/navigator/index.html?&_ga=2.48248804.337210607.1673989679-241632404.1672853064&_gac=1.17025355.1673455980.CjwKCAiA2fmdBhBpEiwA4CcHzfI2w1_D95zAr3_d6QTypOMXGTpUxtS06c55inucNwZvUZn4AebsJxoCZEgQAvD_BwE&_gl=1*elem6v*_ga*MjQxNjMyNDA0LjE2NzI4NTMwNjQ.*_ga_GVK9ZHZSMR*MTY3Mzk5NDQzOS4zMS4xLjE2NzM5OTQ3MDcuMC4wLjA.#logging-in-as-a-party).


### IV. Compiling & Testing
To compile and test, run the pre-written script in the `Test.daml` under /daml OR run:
```
$ daml start
```