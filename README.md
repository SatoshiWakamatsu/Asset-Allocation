# Asset-Allocation
To calculate an ideal asset allocation

I am an individual investor and a Popular Investor on eToro.
I invest mainly in technology and want to learn more about coding to understand better.
I have learnt some basic Python from Skillshare and use Python3 IDLE to code.
As a practice, I am coding my algorithm to determine the ideal allocation and purchase price of stocks.

class Stock:
    def __init__(self, ticker, peak, current, risk, alloc):
        self.ticker = ticker
        self.peak = peak
        self.current = current
        self.risk = risk
        self.alloc = alloc

    def Risk(self):
        print(self.risk)

total_alloc = 103

aapl = Stock("AAPL",  157.26,  151.00,  4.14,   8)
amd  = Stock(" AMD",  155.65,  152.45,  5.34,   4)
msft = Stock("MSFT",  340.66,  339.51,  4.64,  10)
nvta = Stock("NVTA",   61.59,   21.91,  9.23, 4.6)
okta = Stock("OKTA",  294.00,  267.95,  6.68,   6)
pins = Stock("PINS",   89.90,   48.79,  7.98,   6)
pton = Stock("PTON",  171.00,   54.85, 11.60, 6.6)
qcom = Stock("QCOM",  183.73,  181.81,  4.96,   8)
run  = Stock(" RUN",  100.93,   55.98,  5.69,   3)
se   = Stock("  SE",  372.70,  310.00,  5.58,   4)
sedg = Stock("SEDG",  377.00,  360.50,  4.18,   3)
shop = Stock("SHOP", 1704.39, 1675.32,  3.70,   3)
sq   = Stock("  SQ",  289.23,  238.47,  7.08,   5)
tdoc = Stock("TDOC",  308.00,  135.99,  8.32, 5.6)
tsla = Stock("TSLA", 1243.49, 1054.73,  7.08,   5)
ttd  = Stock(" TTD",  111.82,  111.64,  2.84,   2)


lst = [aapl, amd, msft, nvta, okta, pins, pton, qcom, run, se, sedg, shop, sq, tdoc, tsla, ttd]

#print(lst)

#aapl.Risk()

#print(lst[0].ticker)

#print(round(aapl.risk/aapl.alloc,2))

sum_avrrisk = 0
lst_avrrisk = []

for x in lst:
    x.avrrisk = round(x.alloc / x.risk,4)
    sum_avrrisk = sum_avrrisk + x.avrrisk
    lst_avrrisk.append(x.avrrisk)

Sum = round(sum(lst_avrrisk),4)

print(Sum)



print(sum_avrrisk)
print("TICK", "Ideal", "Diff")

for x in lst:
    x.ideal_ratio = round(x.avrrisk/sum_avrrisk,3)
    x.ideal_alloc = round(x.ideal_ratio * total_alloc)
    x.diff = round(x.alloc - x.ideal_alloc,1)
    x.ideal_alloc_text = f"{x.ideal_alloc:>5}"
    x.diff_text = f"{x.diff:>4}"
    print(x.ticker, x.ideal_alloc_text, x.diff_text)
