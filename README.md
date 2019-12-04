# BAII-PLUS-Calculator

## Discounting Payments to Present Value

### discount(pmt,i,n)
pmt = payment  
i = interest rate  
n = duration  

ex: discount(100,5,10) is discounting a payment of 100 back 10 years by 5%. This function is used as a helper function in the main baii function, but can be used for smaller problems. 

## Accumulating Payments to Future Value

### accumulate(pmt,i,n)
pmt = payment  
i = interest rate  
n = duration  

ex: accumulate(100,5,10) is accumulating a payment of 100 10 years ahead by 5%. This function is used as a helper function in the main baii function, but can be used for smaller problems. 

# Annuities

![AnnuityImmediate](https://github.com/mackenziemitchell6/Actuarial/blob/master/annImmediate.png "Annuity Immediate") 

![AnnuityDue](https://github.com/mackenziemitchell6/Actuarial/blob/master/annDue.png "Annuity Due") 

## a angle n at i (present value of annuity immediate)

### a(n,i)
n = duration  
i = interest rate  

ex: 3000*(a(8,1.5)) = 22,457.78 and is calculating the present value of an annuity immediate with
payments of 3000 accumulated at 1.5% for 8 years

## a double dot angle n at i (present value of annuity due)

### a_(n,i)
n = duration  
i = interest rate  
 
 ex: 4*(a_(3,5)) = 11.44 and is calculating the present value of an annuity due with
payments of 4 accumulated at 5% for 3 years


## s angle n at i (future value of annuity immediate)

### s(n,i)
n = duration  
i = interest rate  

ex: 1000*(s(60,1.625)) = 100336.676 and is calculating the future value of an annuity immediate with
payments of 1000 accumulated at 1.625% for 60 years


## s double dot angle n at i (future value of annuity due)

### s_(n,i)
n = duration  
i = interest rate  

ex: 4*(s_(3,5)) = 13.2405 and is calculating the future value of an annuity due with
payments of 4 accumulated at 5% for 3 years

## Interest Rate for Increasing Payments Annuity 

### i_increasing_pmt(i,g)
i = interest rate  
g = growth rate  

ex: increasing_pmt(5,3) = 1.9417 and is calculating the interest rate that should be used to calculate
present of future values for an annuity at 5% that is steadily increasing by 3%. This function is used as a helper function in the main baii class, but can be used for smaller problems. 

## Present Value of Uneven Cashflows

## Most of the variables in this function can be solved for. Set the variable that you wish to solve for as 'solve'.

### unequal_pmts(pmts=[],i=5,pv=0,fv=0,bng=False)

pmts = list of payment schedule (default: pmts = [] empty list. Please enter a list of the cash flow payment schedule). [This variable may not be solved for in this function.]  
i = interest rate (default: i = 5. Please change interest rate as needed)  
pv = present value (default: pv = 0. Please change present value as needed, a common value for this variable is pv = 'solve').  
fv = future value (default: fv = 0. Please change future value as needed, a common value for this variable is fv = 'solve').  
bng = beginning (default: bng = False. Use bng = True for annuity due)  

ex: unequal_pmts(list((400,300,250)),i=5,pv='solve') = 869.0206 and is calculating the present value of payments of 400, 300, and 250 at 5%.

## Financial Calculator with Increasing Payments Capabilities

### baii(n=None,i=5,pv=0,pmt=0,fv=0,bng=False, increasing=0)
n = duration
i = interest rate (default: i = 5. Please change interest rate as needed)  
pv = present value (default: pv = 0. Please change present value as needed, a common value for this variable is pv = 'solve').  
fv = future value (default: fv = 0. Please change future value as needed, a common value for this variable is fv = 'solve').  
bng = beginning (default: bng = False. Use bng = True for annuity due)  
increasing = growth rate, if applicable (default: increasing = 0. Please replace with a periodic growth rate such as 5)  

ex: Your uncle is retiring tomorrow when he turns 65. He expects to live for
another 20 years. He has accumulated $1 million in his retirement
account and would like to start making annual withdrawls tomorrow to
support his retirement. The accoune earns 5% annually and your uncle
would like to increase his withdrawls by 3% every year to account for inflation.
How much should he withdraw tomorrow?

baii(n=20,i=5,pv=1000000,pmt='solve',bng=True,increasing=3) = 59655.1121

ex: How much would I have to deposit in an account today that pays 12%
interest compounded quarterly, so that I have a balance of 20,000 in the
account at the end of 10 years?

baii(n=40,i=3,pv='solve',fv=20000) = 6131.1368

or, solving for the interest rate

baii(n=40,i='solve',pv=6131.68,fv=20000) = 2.99977

ex: How much money must you deposit now at 6% interest compounded 
quarterly in order to be able to withdraw $3,000 at the end of 
each quarter year for two years? 

baii(n=8,i=1.5,pmt=3000,pv='solve') = 22457.7752

ex: Suppose you invested $1000 per quarter over a 15 year period. 
If money earns an annual rate of 6.5% compounded quarterly, 
how much would be available at the end of the time period?

baii(n=60,i=1.625,pmt=1000,fv='solve') = 100336.67614

Another way to solve this problem:

1000*(s(60,1.625)) = 100336.67614

ex: Determine the accumulated value of a 3-year annuity due with annual 
payments of 4 using an annual effective interest rate of 5%

baii(n=3,pmt=4,i=5,bng=True,fv='solve') = 13.2405

Another way to solve this problem:

4*(s_(3,5)) = 13.2405

Another way to solve this problem:

accumulate(4*(a_(3,5)),5,3) = 13.2405

ex: annuity due of 5 years with 5% aeir with payments of 100

baii(n=5,i=5,pmt=100,bng=True,pv='solve') = 454.595

