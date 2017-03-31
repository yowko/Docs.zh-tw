---
title: "如何：從 XmlReader 串流 XML 片段 (C#) | Microsoft Docs"
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
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4bb11e120a123b701e45916b983032797c0ea8b6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>如何：從 XmlReader 串流 XML 片段 (C#)
當您必須處理大型 XML 檔案時，可能無法將整個 XML 樹狀載入記憶體中。 這個主題示範如何使用 <xref:System.Xml.XmlReader> 串流片段。  
  
 使用 <xref:System.Xml.XmlReader> 讀取 <xref:System.Xml.Linq.XElement> 物件的其中一個最有效方式，就是撰寫您自己的自訂座標軸方法。 座標軸方法通常會傳回集合，例如 <xref:System.Xml.Linq.XElement> 的 <xref:System.Collections.Generic.IEnumerable%601>，如本主題的範例中所示。 在自訂座標軸方法中，呼叫 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法來建立 XML 片段後，使用 `yield return` 傳回集合。 這會將延後執行語意 (Semantics) 提供給您自訂的座標軸方法。  
  
 當您從 <xref:System.Xml.XmlReader> 物件建立 XML 樹狀結構時，<xref:System.Xml.XmlReader> 必須置放在某個項目上。 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法在讀取項目的結尾標記前不會傳回。  
  
 如果您想要建立部分樹狀結構，您可以具現化 <xref:System.Xml.XmlReader>、將讀取器置放在您要轉換成 <xref:System.Xml.Linq.XElement> 樹狀結構的節點上，然後建立 <xref:System.Xml.Linq.XElement> 物件。  
  
 [如何：串流 XML 片段並存取標頭資訊 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) 主題包含如何串流更複雜文件的資訊與範例。  
  
 [如何：執行大型 XML 文件的串流轉換 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) 主題包含使用 LINQ to XML 轉換非常大的 XML 文件，同時維護小的記憶體使用量的範例。  
  
## <a name="example"></a>範例  
 這個範例會建立自訂座標軸方法。 您可以使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢進行查詢。 自訂座標軸方法  `StreamRootChildDoc` 是一種方法，特別針對讀取具有重複 `Child` 項目的文件而設計。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 這個範例會產生下列輸出：  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 在此範例中，來源文件很小。 但是，即使有數百萬的 `Child` 元素，此範例的記憶體使用量還是很小。  
  
## <a name="see-also"></a>另請參閱  
 [剖析 XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
