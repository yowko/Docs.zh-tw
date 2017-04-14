---
title: "System.Math 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# System.Math 方法
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援下列 <xref:System.Math> 方法。  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=fullName>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=fullName>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=fullName>  
  
## 與 .NET 的差異  
 .NET Framework 使用的捨入語意 \(Semantics\) 與 SQL Server 不同。  .NET Framework 中的 <xref:System.Math.Round%2A> 方法會執行「*四捨六入五成雙*」\(Banker's Rounding\)，將結尾為 .5 的數字捨入或進位為最接近的偶數，而不是下一個較高的位數。  例如，2.5 會捨入為 2，而 3.5 會進位為 4   \(當資料交易很大時，此法有助於避免系統性地偏向較高位數的值\)。  
  
 在 SQL 中，`ROUND` 函式則會一律往遠離 0 的方向捨入。  因此 2.5 會捨入為 3，這與 .NET Framework 中捨入為 2 相反。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會採用 SQL `ROUND` 語意，不會嘗試實作 Banker's Rounding \(四捨六入五成雙\)。  
  
## 請參閱  
 [資料型別和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)