# Disclaimer

**The purpose of this repository is to provide clear instructions and guidelines for Daml learners to pass the Daml Fundamentals certification via their capstone project. Please bear in mind that any code within is provided for illustrative purposes only, and as such may not be production quality and/or may not fit your use-cases. You may use the contents of this repository in parts or in whole according to the BSD0 license:**

---

# 🛠️ Fast Food Restaurant 🛠️ 
This is an application to order food at a fast food restaurant built in Daml.

### I. Overview 
This project was created by using the `creat-daml-app` template. 

Proposer can create a ProjectProposal contract. Evaluator can exercise ProposerAccomplishments to confirm if the proposer is ready to take on the new project. Evaluator can either Reject or Approve the proposal. Upon getting rejected, proposer can exercise Revise to re-propose the project with updated details. Upon getting approved, a Project contract is created, which then evaluator can Evaluate to create an Accomplishmen contract with, if the Project contract is considered ready to be published.


### II. Workflow
  1. Customer creates an Order contract     
  2. Restaurant exercises StartOrder if they want to take an order from the customer.
  3. Customer exercises AddItems with a list of (item, amount) they want to order. The items that exist with a valid amount are added.
  4. Customer exercises ApplyDiscounts with a code. The discount is applied if a valid code with the key exists. 
  5. Customer exercises PayOrder with an amount. Rejected if not enough money, accepted if enough. 
  6. Restaurant exercises ServeOrder. 
  7. Customer exercises PickUp order. Error if restaurant has not served it, fine otherwise. 

### III. Challenge(s)
* `controller ... can` syntax causes warning in Daml 2.0+. The code itself does not cause any issues/errors in 2.5.0 but according to the warning, the syntax will be deprecated in the future versions of Daml. More information [here](https://docs.daml.com/daml/reference/choices.html#daml-ref-controller-can-deprecation).
* The new controller syntax requires a controller to be an observer first before they can exercise a choice, otherwise it'll throw an error: "Attempt to fetch or exercise a contract not visible to the committer." For more information, check out [this post](https://discuss.daml.com/t/error-attempt-to-fetch-or-exercise-a-contract-not-visible-to-the-committer/1304/1) on the Daml Forum.
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