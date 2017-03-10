---
title: "Structures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "structures"
  - "user-defined data types, structures"
  - "user-defined types, about user-defined types"
  - "data types [Visual Basic], user-defined"
  - "user-defined data types, about user-defined data types"
  - "types [Visual Basic], user-defined"
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*結構*」\(Structure\) 是廣義的使用者定義型別 \(UDT\)，由舊版 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 支援。  除了欄位之外，結構還公開屬性、方法及事件。  結構可以實作一或多個介面，而您可以宣告每個欄位各自的存取層級。  
  
 您可以組合不同型別的資料項目，以建立結構。  結構會將一或多個「*項目*」\(Element\) 彼此產生關聯，再與結構本身產生關聯。  當您宣告結構時，它會變成「*複合資料型別*」\(Composite Data Type\)，接著可以宣告該型別的變數。  
  
 當您希望單一變數能夠存放幾種相關資訊時，結構就能發揮相當的作用。  例如，您可能要將員工的姓名、電話分機號碼及薪資放在一起。  針對此資訊，您可以使用幾個變數，或是您也可以定義結構並將其當成單一的員工變數來使用。  當您有許多員工以及隨之產生的許多變數執行個體時，結構的好處就變得相當明確。  
  
## 在本節中  
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 說明如何宣告結構及它的項目。  
  
 [Structure Variables](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 涵蓋如何將結構指派至變數並存取它的項目。  
  
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 摘要結構如何與陣列、物件、程序及彼此之間進行互動。  
  
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 說明結構與類別的相似及相異處。  
  
## 相關章節  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 介紹 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 資料型別並說明用法。  
  
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 列出 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供的基礎資料型別。