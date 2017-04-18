---
title: "System.String 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# System.String 方法
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援下列 <xref:System.String> 方法。  
  
## 一般不支援的 System.String 方法  
 一般不支援的 <xref:System.String> 方法：  
  
-   文化特性感知 \(Culture\-Aware\) 多載 \(取用 `CultureInfo`\/`StringComparison`\/`IFormatProvider` 的方法\)。  
  
-   取用或產生 `char` 陣列的方法。  
  
## 不支援的 System.String 靜態方法  
  
|不支援的 System.String 靜態方法|  
|-----------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=fullName>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=fullName>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=fullName>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=fullName>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=fullName>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=fullName>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|<xref:System.String.Format%2A?displayProperty=fullName>|  
|<xref:System.String.Join%2A?displayProperty=fullName>|  
  
## 不支援的 System.String 非靜態方法  
  
|不支援的 System.String 非靜態方法|  
|------------------------------|  
|[String.IndexOfAny\(Char\<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=fullName>|  
|<xref:System.String.Split%2A?displayProperty=fullName>|  
|<xref:System.String.ToCharArray?displayProperty=fullName>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=fullName>|  
|[String.TrimEnd\(Char\<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=fullName>|  
|[String.TrimStart\(Char\<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=fullName>|  
  
## 與 .NET 的差異  
  
-   查詢不會考慮伺服器上可能作用中的 SQL Server 定序 \(Collation\)，因此預設會提供區分文化特性、但不區分大小寫的比較。  這個行為與 .NET Framework 的預設區分大小寫語意 \(Semantics\) 不同。  
  
-   當 `LastIndexOf` 傳回 0 時，表示字串是 `NULL`，或找到的位置是 0。  
  
-   固定長度字串 \(`CHAR`、`NCHAR`\) 上的串連或其他作業可能會傳回未預期的結果，原因是這些型別已自動將填補套用至資料庫中。  
  
-   因為許多方法 \(如 `Replace`、`ToLower`、`ToUpper` 和字元索引子 \(Indexer\)\) 都沒有 `TEXT` 或 `NTEXT` 資料行和 XML 的有效轉譯，所以如果正常轉譯，則會發生 `SqlExceptions`。  對這些型別而言，這個行為是可接受的行為。  不過，所有字串作業都必須符合 `VARCHAR`、`NVARCHAR`、`VARCHAR(max)` 和 `NVARCHAR(max)` 的 Common Language Runtime \(CLR\) 語意。  
  
## 請參閱  
 [資料型別和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)