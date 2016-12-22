---
title: "Accessing XML in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "LINQ to XML [Visual Basic], accessing XML"
  - "Visual Basic code, XML"
  - "accessing XML [Visual Basic], axis properties"
  - "XML [Visual Basic], axis properties"
  - "XML [Visual Basic], accessing"
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Accessing XML in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 提供 XML 軸屬性以存取及巡覽 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 結構。  這些屬性使用特殊語法，可讓您經由指定 XML 名稱，存取項目和屬性 \(Attribute\)。  
  
 下表列出可以讓您存取 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中 XML 項目和屬性的語言功能。  
  
### XML 軸屬性  
  
|屬性說明|範例|描述|  
|----------|--------|--------|  
|*子項軸屬性 \(Child Axis\)*|`contact.<phone>`|取得所有 `phone` 項目，這些項目是 `contact` 項目的子項目。|  
|*屬性軸屬性 \(Attribute Axis\)*|`phone.@type`|取得 `phone` 項目的所有 `type` 屬性 \(Attribute\)。|  
|*子代軸屬性 \(Descendant Axis\)*|`contacts...<name>`|取得 `contacts` 項目的所有 `name` 項目，無論其出現在多深的階層架構中。|  
|*擴充索引子屬性 \(Extension Indexer\)*|`contacts...<name>(0)`|取得序列中的第一個 `name` 項目。|  
|*值*|`contacts...<name>.Value`|取得序列中第一個物件的字串表示，如果序列是空的則為 `Nothing`。|  
  
## 在本節中  
 [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 顯示如何使用子代軸屬性存取具有指定名稱以及包含在 XML 項目下的所有 XML 項目。  
  
 [How to: Access XML Child Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 顯示如何使用子項軸屬性 \(Property\) 存取 XML 項目中具有所指定名稱的所有 XML 子項目。  
  
 [How to: Access XML Attributes](../Topic/How%20to:%20Access%20XML%20Attributes%20\(Visual%20Basic\).md)  
 顯示如何使用屬性 \(Attribute\) 軸屬性 \(Property\) 存取 XML 項目中具有所指定名稱的所有 XML 屬性 \(Attribute\)。  
  
 [How to: Declare and Use XML Namespace Prefixes](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 顯示如何宣告 XML 命名空間前置字元並使用它來建立及存取 XML 項目。  
  
## 相關章節  
 [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 提供說明各種 XML 存取屬性的章節連結。  
  
 [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 提供在 Visual Basic 中使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的簡介。  
  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 提供在 Visual Basic 中使用 XML 常值的簡介。  
  
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 提供在 Visual Basic 中載入及修改 XML 的相關章節連結。  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 提供說明如何在 Visual Basic 中使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的章節連結。