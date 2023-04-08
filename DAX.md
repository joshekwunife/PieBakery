AverageRevenue = AVERAGE(FactTable[Cost])

CummRevenue = CALCULATE([TotalRevenue], FILTER(ALLSELECTED('Calendar'), 'Calendar'[Date] <= MAX('Calendar'[Date])))

FirstTransactionDate = MAX(FactTable[Order Date])

InStoreTotal = CALCULATE([TotalRevenue], DimOrderType[Pre-Order/In-Store Purchase]="In-Store")

PreOrderTotal = CALCULATE([TotalRevenue], DimOrderType[Pre-Order/In-Store Purchase]="Pre-order")

Revenue2020 = CALCULATE([TotalRevenue], 'Calendar'[Year] = "2020")

Revenue2021 = CALCULATE([TotalRevenue], 'Calendar'[Year] = "2021")

Today = TODAY() --ForCurrentDate

TotalOrders = SUM(FactTable[Quantity])

TotalRevenue = SUM(FactTable[Cost])

TotalTransactions = COUNTROWS(FactTable)

YearlyDifference = 
    var Revenue2020= 
        CALCULATE(SUM(FactTable[Cost]), 'Calendar'[Year] = 2020
        )
    var Revenue2021 =
        CALCULATE(SUM(FactTable[Cost]), 'Calendar'[Year] = 2021
        )
    var result =
        [Revenue2021] - [Revenue2020]
    RETURN
    result
