---
title: "功能性程序性程式設計 (LINQ to XML) (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9d5afe31c8c81f4b099853a5e6e274156a1baa7f
ms.lasthandoff: 03/13/2017

---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>功能性程序性程式設計 (LINQ to XML) (Visual Basic)
XML 應用程式有很多種：  
  
-   有些應用程式會採用 XML 來源文件，然後以不同於來源文件的組織結構產生新的 XML 文件。  
  
-   有些應用程式會採用 XML 來源文件，然後以完全不同的形式 (例如，HTML 或 CSV 文字檔)，產生結果文件。  
  
-   有些應用程式會採用 XML 來源文件，然後將記錄插入到資料庫中。  
  
-   有些應用程式會從其他來源 (例如，資料庫) 取得資料，然後從其中建立 XML 文件。  
  
 這些並非 XML 應用程式的全部類型，但是這些是 XML 程式設計人員必須實作的一組代表性的功能類型。  
  
 利用所有這些應用程式類型，開發人員可以採用兩種明顯不同的方法：  
  
-   使用宣告式方法的功能結構。  
  
-   使用程序性程式碼進行記憶體中 XML 樹狀結構修改。  
  
 LINQ to XML 同時支援這兩種方法。  
  
 使用功能性方法時，您可以撰寫採用來源文件的轉換，然後利用所需的組織結構產生全新的結果文件。  
  
 就地修改 XML 樹狀結構時，您可以撰寫可在記憶體中 XML 樹狀結構內周遊與導覽程式碼的程式碼，藉以在必要時插入、刪除與修改程式碼。  
  
 您可以搭配任一種方法使用 LINQ to XML。 您可以使用相同的類別，在某些情況下，也可以使用相同的方法。 但是，兩種方法的結構與目標差異相當大。 例如，在不同的情況下，其中一種方法的效能通常會比較好，而且或多或少會使用到記憶體。 此外，其中一種方法會比較容易撰寫，並產生較容易維護的程式碼。  
  
 若要查看兩種對照的方法，請參閱[記憶體中 XML 樹狀結構修改與。功能建構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)。  
  
 如需撰寫功能性轉換的教學課程，請參閱[純功能性轉換的 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 程式設計概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
