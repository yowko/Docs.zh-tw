---
title: "不支援的功能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 不支援的功能
在 LINQ to SQL 中，下列 SQL 功能無法透過轉譯現有 Common Language Runtime \(CLR\) 和 .NET Framework 建構來公開 \(Expose\)：  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     雖然 `LIKE` 並非透過直接轉譯提供支援，但是類似的功能存在 <xref:System.Data.Linq.SqlClient.SqlMethods> 類別 \(Class\) 中。  如需詳細資訊，請參閱[M:System.Data.Linq.SqlClient.SqlMethods.Like\(System.String,System.String](assetId:///M:System.Data.Linq.SqlClient.SqlMethods.Like(System.String,System.String?qualifyHint=True&autoUpgrade=True)。  
  
-   `DATEDIFF`  
  
     LINQ to SQL 對於 `DATEDIFF` 的支援有限。  類似的功能存在 [SqlMethods](assetId:///T:System.Data.Linq.SqlClient.SqlMethods?qualifyHint=False&autoUpgrade=True) 類別中。  
  
-   `ROUND`  
  
     LINQ to SQL 對於 `ROUND` 的支援有限。  如需詳細資訊，請參閱[System.Math 方法](../Topic/System.Math%20Methods.md)。  
  
## 請參閱  
 [資料型別和函式](../Topic/Data%20Types%20and%20Functions.md)