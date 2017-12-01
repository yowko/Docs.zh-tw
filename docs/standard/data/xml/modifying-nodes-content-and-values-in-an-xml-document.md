---
title: "修改 XML 文件中的節點、內容和值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 00b923edb95852d9434db1b393df68fd9d0c8a1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>修改 XML 文件中的節點、內容和值
有許多方法可以修改文件中的節點及內容。 您可以：  
  
-   使用 <xref:System.Xml.XmlNode.Value%2A> 屬性變更節點的值。  
  
-   藉由以新節點取代節點，修改整個節點集。 這可以使用 <xref:System.Xml.XmlNode.InnerXml%2A> 屬性來完成。  
  
-   使用 <xref:System.Xml.XmlNode.RemoveChild%2A> 方法，以新節點取代現有節點。  
  
-   使用 <xref:System.Xml.XmlCharacterData>、<xref:System.Xml.XmlCharacterData.AppendData%2A> 或 <xref:System.Xml.XmlCharacterData.InsertData%2A> 方法，將其他字元加入繼承自 <xref:System.Xml.XmlCharacterData.ReplaceData%2A> 類別的節點。  
  
-   使用繼承自 <xref:System.Xml.XmlCharacterData.DeleteData%2A> 之節點型別上的 <xref:System.Xml.XmlCharacterData> 方法，藉由移除某範圍的字元來修改內容。  
  
 變更節點值的簡單技術是使用 `node.Value = "new value";`。 下表列出此單行程式碼適用的節點型別，以及該節點型別已變更的確切資料。  
  
|節點類型|變更的資料|  
|---------------|------------------|  
|屬性|屬性的值。|  
|CDATASection|CDATASection 的內容。|  
|註解|註解的內容。|  
|ProcessingInstruction|內容 (目標除外)。|  
|Text|文字的內容。|  
|XmlDeclaration|宣告的內容 (`<?xml` 及 `?>` 標記除外)。|  
|Whitespace|泛空白字元的值。 該值可以設為四個可以辨識的 XML 空白字元其中之一：空格、定位字元、CR 或 LF。|  
|SignificantWhitespace|顯著泛空白字元的值。 該值可以設為四個可以辨識的 XML 空白字元其中之一：空格、定位字元、CR 或 LF。|  
  
 未列在表格中的任何節點型別都是無效節點型別，不可設定值。 在任何其他節點型別上設定值都會擲回 <xref:System.InvalidOperationException>。  
  
 <xref:System.Xml.XmlNode.InnerXml%2A> 屬性會變更目前節點之子節點的標記。 設定此屬性，會以指定字串的已剖析內容取代子節點。 剖析會在目前命名空間內容中完成。 此外，<xref:System.Xml.XmlNode.InnerXml%2A> 會移除多餘的命名空間宣告。 因此，大量的剪貼作業並不會因為有多餘的命名空間宣告，而增加文件大小。 如需顯示 <xref:System.Xml.XmlNode.InnerXml%2A> 作業上命名空間效果的程式碼範例，請參閱 <xref:System.Xml.XmlDocument.InnerXml%2A> 屬性。  
  
 當使用 <xref:System.Xml.XmlCharacterData.ReplaceData%2A> 及 <xref:System.Xml.XmlNode.RemoveChild%2A> 方法時，方法會傳回已取代或已移除的節點。 然後，可以將此節點重新插入至 XML 文件物件模型 (DOM) 中的任何其他位置。 <xref:System.Xml.XmlCharacterData.ReplaceData%2A> 方法會在插入至文件的節點上進行兩個驗證檢查。 第一個檢查可確保該節點已成為可以擁有其型別子節點之節點的子項。 第二個檢查可確保插入的節點不是其成為子項之節點的上階。 違反任何一個條件，都會擲回 <xref:System.InvalidOperationException>。  
  
 在可編輯之節點中加入或移除唯讀子節點有效。 不過，嘗試修改唯讀節點本身會擲回 <xref:System.InvalidOperationException>。 修改 <xref:System.Xml.XmlEntityReference> 節點的子節點便是一個範例。 子節點是唯讀的，而且無法修改。 對其進行修改的任何嘗試，都會擲回 <xref:System.InvalidOperationException>。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
