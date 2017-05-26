---
title: "功能性與程序性程式設計的比較 (LINQ to XML) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4505d705b82e7d803070153a107f2f6117a0130a
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>功能性與程序性程式設計的比較 (LINQ to XML) (C#)
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
  
 若要查看這兩種對照方法，請參閱[記憶體中 XML 樹狀結構修改與函數式建構的比較 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)。  
  
 如需撰寫功能性轉換的教學課程，請參閱 [XML 的純功能性轉換 (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 程式設計概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
