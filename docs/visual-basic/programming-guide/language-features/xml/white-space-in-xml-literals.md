---
title: "White Space in XML Literals (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "white space [XML in Visual Basic]"
  - "XML literals [Visual Basic], white space"
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# White Space in XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器在建立 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件時，只會包含 XML 常值中顯著的泛空白字元。  不會包含不顯著的泛空白字元。  
  
## 顯著和不顯著的泛空白字元  
 XML 常值中的泛空白字元只有在 3 個區域是顯著的：  
  
-   在屬性 \(Attribute\) 值中。  
  
-   屬於項目文字內容的一部分且文字也包含其他字元。  
  
-   在項目文字內容的內嵌運算式中。  
  
 否則，編譯器會將泛空白字元視為不重要，而且不會將常值中的這些泛空白字元加入 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件中。  
  
 若要加入 XML 常值中不顯著的泛空白字元，請使用包含字串常值並具有泛空白字元的內嵌運算式。  
  
> [!NOTE]
>  如果 `xml:space` 屬性顯示在 XML 項目常值中，則 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將該屬性加入至 <xref:System.Xml.Linq.XElement> 物件，但是加入此屬性並不會變更編譯器處理泛空白字元的方式。  
  
## 範例  
 下列範例包含兩個 XML 項目：外部及內部。  這兩個項目在其文字內容中都包含泛空白字元。  外部項目的泛空白字元是不顯著的，因為它只包含泛空白字元和 XML 項目。  內部項目的泛空白字元則是顯著的，因為它包含泛空白字元和文字。  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 當程式碼執行時，會顯示下列文字。  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## 請參閱  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)