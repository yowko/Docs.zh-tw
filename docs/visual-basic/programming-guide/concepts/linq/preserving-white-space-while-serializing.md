---
title: Serializing2 時保留空白字元
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: 8a69916627c25e4c90131e5eb9a1939bb6dea207
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373994"
---
# <a name="preserving-white-space-while-serializing"></a>序列化時保留空白字元
本主題描述如何在序列化 XML 樹狀結構時控制空白字元。  
  
 常見的案例為讀取縮排的 XML、建立沒有任何空白字元文字節點 (也就是不保留空白字元) 的記憶體中 XML 樹狀結構、在 XML 上執行某些作業，然後儲存包含縮排的 XML。 當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。 這是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的預設行為。  
  
 其他常見案例為讀取與修改已經過刻意縮排的 XML。 您可能不想用任何方式變更這個縮排。 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，如果您在載入或剖析 XML 時保留空白字元，並在序列化 XML 時停用格式化，就可以達到這個效果。  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>序列化 XML 樹狀結構之方法的空白字元行為  
 下列 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 類別中的方法會序列化 XML 樹狀結構。 您可以將 XML 樹狀結構序列化至檔案、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader>。 `ToString` 方法會序列化至字串。  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
-   [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 如果此方法不採用 <xref:System.Xml.Linq.SaveOptions> 當做引數，該方法將會格式化 (縮排) 序列化的 XML。 在此情況下，會宣告 XML 樹狀結構中的所有有效空白字元。  
  
 如果此方法採用 <xref:System.Xml.Linq.SaveOptions> 當做引數，您就可以指定該方法不格式化 (縮排) 序列化的 XML。 在此情況下，會保留 XML 樹狀中的所有空白字元。  
  
## <a name="see-also"></a>另請參閱
- [序列化 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
