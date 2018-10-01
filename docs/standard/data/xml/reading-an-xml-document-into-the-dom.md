---
title: 將 XML 文件讀取到 DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9031f5df0d0f48dc2844cdfd0654ee4ab876cc22
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47399043"
---
# <a name="reading-an-xml-document-into-the-dom"></a>將 XML 文件讀取到 DOM
從不同的格式將 XML 資訊讀取到記憶體。 可從字串、資料流、URL、文字讀取器或衍生自 <xref:System.Xml.XmlReader> 的類別讀取它。  
  
 <xref:System.Xml.XmlDocument.Load%2A> 方法將文件引入記憶體，並擁有可從各個不同格式取得資料的多載方法。 另外還有一個 <xref:System.Xml.XmlDocument.LoadXml%2A> 方法，可從字串讀取 XML。  
  
 不同的 <xref:System.Xml.XmlDocument.Load%2A> 方法會影響載入 XML 文件物件模型 (DOM) 時建立的節點。 下表列出某些 <xref:System.Xml.XmlDocument.Load%2A> 方法及說明這些方法之主題間的差異。  
  
|主旨|主題|  
|-------------|-----------|  
|建立泛空白字元節點|用來載入 DOM 的物件會影響在 DOM 中產生的泛空白字元及顯著泛空白字元節點。 如需詳細資訊，請參閱[載入 DOM 時處理泛空白字元和顯著泛空白字元](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md)。|  
|從特定節點開始載入 XML 或載入整個 XML 文件|使用 <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> 方法可將資料從特定節點載入至 DOM。 如需詳細資訊，請參閱[從讀取器載入資料](../../../../docs/standard/data/xml/load-data-from-a-reader.md)。|  
|載入 XML 時進行驗證|可在將 XML 資料載入至 DOM 時對其進行驗證。 使用驗證 <xref:System.Xml.XmlReader> 來完成此作業。 如需在載入 XML 時進行驗證的詳細資訊，請參閱[驗證 DOM 中的 XML 文件](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)。|  
  
 下列範例顯示以 <xref:System.Xml.XmlDocument.LoadXml%2A> 方法載入的 XML，以及隨後儲存至稱為 `data.xml` 之文字檔的資料。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
