---
title: "System.Object 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# System.Object 方法
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援下列 <xref:System.Object> 方法。  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=fullName>|  
|<xref:System.Object.ToString?displayProperty=fullName>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援下列 <xref:System.Object> 方法。  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=fullName>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=fullName>|  
|<xref:System.Object.MemberwiseClone?displayProperty=fullName>|<xref:System.Object.GetType?displayProperty=fullName>|  
|二進位型別 \(例如 `BINARY`、`VARBINARY`、`IMAGE` 和 `TIMESTAMP`\) 的 <xref:System.Object.ToString?displayProperty=fullName>。||  
  
## 與 .NET 的差異  
 Double 的 <xref:System.Object.ToString?displayProperty=fullName> 輸出會將 SQL `CONVERT`\(NVARCHAR\(30\), @x, 2\) 用於 SQL。  在此情況下，SQL 一律會使用 16 位數和科學記號表示法 \(例如，"0.000000000000000e\+000" 代表 0\)。  因此，<xref:System.Object.ToString?displayProperty=fullName> 轉換不會產生與 .NET Framework 中 <xref:System.Convert.ToString%2A?displayProperty=fullName> 相同的字串。  
  
## 請參閱  
 [資料型別和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)