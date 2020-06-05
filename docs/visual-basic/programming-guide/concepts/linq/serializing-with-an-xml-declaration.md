---
title: 使用 XML 宣告進行序列化
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: cd303a800efe42d3fa99d601f25d54320570bed3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411790"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>使用 XML 宣告序列化（Visual Basic）
這個主題描述如何控制序列化是否產生 XML 宣告。  
  
## <a name="xml-declaration-generation"></a>XML 宣告產生  
 使用 <xref:System.IO.File> 方法或 <xref:System.IO.TextWriter> 方法序列化為 <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> 會產生 XML 宣告。 當您序列化為 <xref:System.Xml.XmlWriter> 時，寫入器設定 (在 <xref:System.Xml.XmlWriterSettings> 物件中指定) 會決定是否產生 XML 宣告。  
  
 如果您要使用 `ToString` 方法序列化為字串，所產生的 XML 將不會包含 XML 宣告。  
  
### <a name="serializing-with-an-xml-declaration"></a>使用 XML 宣告進行序列化  
 下列範例會建立 <xref:System.Xml.Linq.XElement>、將文件儲存為檔案，然後將檔案列印到主控台：  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>不使用 XML 宣告序列化  
 下列範例顯示如何將 <xref:System.Xml.Linq.XElement> 儲存為 <xref:System.Xml.XmlWriter>。  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>另請參閱

- [序列化 XML 樹狀結構（Visual Basic）](serializing-xml-trees.md)
