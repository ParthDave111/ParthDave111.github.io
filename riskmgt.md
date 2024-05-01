## Risk Management [Automated] for a Bank offering Mortgages for Home 

![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/0aebb2fc-831e-421d-997a-3296b9d600bb)

Business Case:
A work flow was designed to address an ethical challenge for a bank. It was found that for a bank agents were manipulating documents for few commission and providing mortgages that were not ethical. 

This demo project /POC can be very well establised using leveraging low code no code tools like power automate or blue prism. Here I am doing this on python. End to end code is available here [code](https://github.com/ParthDave111/financial-engineering-/blob/main/Bank_mortgage_.ipynb)

Read more about this case: 19.	CBC News. "Real estate agents caught on hidden camera facilitating mortgage fraud for a fee." https://www.cbc.ca/news/business/marketplace-mortgage-fraud-1.6614132.

Risk Management Explained 
1. Risk Gate :Age of customer – As the home mortgages are of long length -25 years and 30 years we have incorporated an algorithm which will remove customer from queue for mortgage if the age is more than 45. Assuming customer get loan at the age of 45, he needs to make payment for next 25 years and he will be 70 by the end of mortgage. In north America average age to retire is 65. Just to be cautious that customer doesn’t default in retiring age this risk check is required. Additional having customer profile like health history and habits can be accounted to make more informed decision. If customer really wants mortgage then he should bring a younger co-signer for mortgage.  
 ![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/bd42d2af-a0b3-485a-a457-d434c98f60a4)

2.Risk Check: FICO SCORE Checking credit score will allow bank to make assessment of credit worthiness of borrower. The higher the score the lower will be the risk of borrower getting default. In the workflow, we have incorporated the same logic. If the customer FICO score is more than 700 then only bank should proceed with an application and if customer score is less than 700 then all the parametric should be assessed. For example number of delinquency, past credit history, previous employement, tax return and other assets and saving check. This risk gate will make sure only reliable borrowers get access to mortgages. 
 ![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/ad937ffd-5544-4557-92d3-5581bb617cbb)

3.Risk Check: Employment Status check – To validate the current borrower is employed either as an self employed or regular employment , in process flow we included this check. This is soft check which means an algorithm will remove customer from the queue for mortgage but not from the application. If customer doesn’t have valid employment status then he/she needs to go to nearest bank.
 ![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/1dc048bf-508f-4be0-89b5-2637c6130313)

Risk assessment -Additional employment check : As in 2024, there are various layoff happening, bank should be cautious with approving mortgage. So we have developed a software which pulls data from twitter and google news with organization having layoff. If an organization had layoff in past 24 months then they will be considered as risky organization and if organization doesn’t have layoff then they will be considered as safe organization. Banks are advised to provide loan by asking the name of employer form the customer and check in database weather the employer is safe or risky 
![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/775bde57-2321-42e0-a637-a5c0be16598f)

![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/170cc8f5-6b26-4346-b256-c204129bf0ef)

4.Risk Check : Anti Money Laundering -It is advised for bank to do a an anti money laundering check. An algorithm is designed which check all previous 3 year data to validate the sources of money and spending pattern to make sure there is no structuring or layering pattern found. If bank discover any such pattern then they should report to respective reporting agency. 
![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/e484942d-8c67-480a-b04e-e295ce22b4ea)

5.Risk Check: Debt to Income ratio – From risk management perspective, it is advisable that bank only provides mortgage to customer which has DTI ratio less than 45. 
 ![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/ea8c8ffd-c4a1-438c-a299-d82f711cfaf3)

6.Risk HEDGE: Mortgage Insurance – It is important that customer put 20% of the money as downpayment for the house. If customer putting less than 20% then bank should insist customer to buy mortgage insurance. Mortgage insurance will hedge if in future house yields to a negative equity. Loan should be postponed or cancelled if customer doesn’t agree to buy mortgage insurance.

 ![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/19cd67b3-edcf-4b84-a498-9bd121cd5114)

7.Risk check- Property appraiser check – Customer might have bought property in fear of missing out and overbidding. It is banks responsibility to do an appraiser check on the property before finalizing the loan. An algorithm is designed which will pull data from government database to find out real value of property. If appraiser value is very large than loan amount then loan should be rejected. Such property would yield to negative equity and customer might stop paying mortgage payments. 
 ![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/29f2f356-e9e4-493a-bbec-05894a4d8dff)

8.Risk Check : Loan to value ratio : After the property is appraised do consider checking loan to value ratio. If Loan to value ratio is less than 80 then the customer has valid property deal in hand and if LTV is more than 80 bank should provide an encouragement to look for fair price property to customer. For LTV ratio more than 85% , it is not advisable for bank to continue and provide mortgage. 
 ![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/ddb15a3c-feb0-44d6-99b3-6aca567d2970)


 

 


