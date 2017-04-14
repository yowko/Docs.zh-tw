---
title: "HOW TO：使用接受參數的預存程序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：使用接受參數的預存程序
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將輸出參數對應至參考參數，而且會針對實值型別 \(Value Type\)，將參數宣告為可為 Null。  
  
 如需如何在查詢中使用輸入參數以傳回資料列集 \(Rowset\) 的範例，請參閱 [HOW TO：傳回資料列集](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)。  
  
## 範例  
 下列範例取用單一輸入參數 \(客戶 ID\)，並傳回輸出參數 \(該客戶的總銷售量\)。  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## 範例  
 您可如下呼叫這個預存程序 \(Stored Procedure\)：  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## 請參閱  
 [預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)   
 [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [用可為 Null 的類型](../Topic/Using%20Nullable%20Types%20\(C%23%20Programming%20Guide\).md)   
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)