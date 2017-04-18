---
title: "命名空間 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 命名空間 (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 導入了命名空間來避免全域識別碼的名稱衝突，例如型別名稱、實體集、函式等等。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的命名空間支援類似於 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 中的命名空間支援。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供了兩種形式的 USING 子句：限定的命名空間 \(為命名空間提供較短的別名\) 及不限定的命名空間，如下列範例所述：  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## 名稱解析規則  
 如果識別項無法在區域範圍內解析，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會嘗試在全域範圍 \(命名空間\) 內尋找名稱。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會先嘗試將此識別項 \(前置詞\) 與其中一個限定的命名空間比對。  如果兩者相符，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會嘗試解析指定之命名空間內的其餘識別項。  如果兩者不相符，則會擲回例外狀況。  
  
 接下來，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會嘗試搜尋所有未限定的命名空間 \(於初構中指定\)，以找出此識別項。  如果可以在剛好一個命名空間內找到此識別項，就會傳回該位置。  如果有一個以上的命名空間符合該識別項，則會擲回例外狀況。  如果無法針對此識別項識別任何命名空間，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會將此名稱傳遞到下一個向外範圍 \(<xref:System.Data.Common.DbCommand> 或 <xref:System.Data.Common.DbConnection> 物件\)，如下列範例所述：  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## 與 .NET Framework 的差異  
 在 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 中，您可以使用部分限定的命名空間。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 則不允許。  
  
## ADO.NET 使用方式  
 查詢是透過 ADO.NET <xref:System.Data.Common.DbCommand> 物件來表示。  <xref:System.Data.Common.DbCommand> 物件則可經由 <xref:System.Data.Common.DbConnection> 物件建置。  此外，命名空間也可以指定成 <xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbConnection> 物件的一部分。  如果 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 無法在查詢本身內解析識別項，則會探查外部命名空間 \(根據類似的規則\)。  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)