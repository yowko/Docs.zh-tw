---
title: "修改 XML 樹狀 (LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de66788186f3ffd09560d8eacdebbbaa5edf067c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>修改 XML 樹狀 (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 是 XML 樹狀結構的記憶體中存放區。 在您從來源載入或剖析 XML 樹狀結構後，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會讓您就地修改該樹狀結構，然後序列化樹狀結構，以便將其儲存到檔案或傳送到遠端伺服器。  
  
 當您就地修改樹狀結構時，您可以使用特定方法，例如，<xref:System.Xml.Linq.XContainer.Add%2A>。  
  
 不過，有另一個方法，就是使用功能結構來產生具有不同組織結構的新樹狀結構。 根據您需要針對 XML 樹狀結構所進行之變更的類型，並根據樹狀結構的大小，這個方法可能更精簡也更容易開發。 本節中的第一個主題會比較這兩個方法。  
  
## <a name="in-this-section"></a>本章節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[記憶體中 XML 樹狀結構修改與功能建構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|比較在記憶體中修改 XML 樹狀與功能結構。|  
|[將項目、 屬性和節點加入至 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|提供將項目、屬性或節點加入到 XML 樹狀的相關資訊。|  
|[修改 XML 樹狀結構中的項目、屬性和節點](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|提供修改現有項目、屬性或節點的相關資訊。|  
|[移除項目、 屬性和節點從 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|提供將項目、屬性或節點從 XML 樹狀移除的相關資訊。|  
|[維護名稱/值組 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|描述如何維護妥善保存為成對名稱/值 (例如，組態資訊或全域設定) 的應用程式資訊。|  
|[如何： 變更整個 XML 樹狀結構 (Visual Basic) 的命名空間](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|顯示如何將 XML 樹狀從一個命名空間移到另一個命名空間。|  
  
## <a name="see-also"></a>另請參閱  
 [程式設計手冊 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
