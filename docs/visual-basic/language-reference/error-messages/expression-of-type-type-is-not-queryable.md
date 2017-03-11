---
title: "Expression of type &lt;type&gt; is not queryable | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36593"
  - "vbc36593"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36593"
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Expression of type &lt;type&gt; is not queryable
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

型別 \<type\> 的運算式無法查詢。請確定您沒有遺漏組件參考及 \(或\) LINQ 提供者的命名空間匯入。  
  
 可查詢的型別是在 <xref:System.Linq>、<xref:System.Data.Linq> 和 <xref:System.Xml.Linq> 命名空間中定義。  您必須匯入其中一個或多個命名空間，以執行 LINQ 查詢。  
  
 <xref:System.Linq> 命名空間可讓您使用 LINQ，查詢集合和陣列這類物件。  
  
 <xref:System.Data.Linq> 命名空間可讓您使用 LINQ，查詢 ADO.NET 資料集和 SQL Server 資料庫。  
  
 <xref:System.Xml.Linq> 命名空間可讓您使用 LINQ 查詢 XML，並使用 Visual Basic 中的 XML 功能。  
  
 **錯誤 ID**：BC36593  
  
### 若要更正這個錯誤  
  
1.  針對 <xref:System.Linq>、<xref:System.Data.Linq> 或 <xref:System.Xml.Linq> 命名空間將 `Import` 陳述式加入程式碼檔。  您也可以使用 \[專案設計工具\] \(\[**我的專案**\]\) 的 \[**參考**\] 頁面，為專案匯入命名空間。  
  
2.  請確定您已識別為查詢來源的型別屬於可查詢的型別。  也就是，實作 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 的型別。  
  
## 請參閱  
 <xref:System.Linq>   
 <xref:System.Data.Linq>   
 <xref:System.Xml.Linq>   
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)