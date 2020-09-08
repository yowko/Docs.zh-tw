---
title: 如何攔截剖析錯誤-LINQ to XML
description: '如果您的 c # 或 Visual Basic 程式嘗試使用 System.xml.linq.xelement> 之類的方法剖析不正確 XML，就可能會發生例外狀況。 您可以撰寫程式來攔截和回應這類例外狀況。'
ms.date: 7/20/2015
dev_langs:
- csharp
- vb
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: f7679bd5a0726c669eb47ad6ad66e0f64259264b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552140"
---
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a>如何 (LINQ to XML 中攔截剖析錯誤) 

本文說明如何在 c # 或 Visual Basic 中偵測格式錯誤或不正確 XML。

LINQ to XML 是使用來執行 <xref:System.Xml.XmlReader> 。 如果將格式不正確或不正確 XML 傳遞給 LINQ to XML，基礎 <xref:System.Xml.XmlReader> 類別將會擲回例外狀況。 剖析 XML 的各種方法（例如 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> ）不會攔截例外狀況; 然後，您的應用程式就可以攔截到例外狀況。

## <a name="example-parse-invalid-xml"></a>範例：剖析不正確 XML

下列程式碼會嘗試剖析不正確 XML。

```csharp
try {
    XElement contacts = XElement.Parse(
        @"<Contacts>
            <Contact>
                <Name>Jim Wilson</Name>
            </Contact>
          </Contcts>");

    Console.WriteLine(contacts);
}
catch (System.Xml.XmlException e)
{
    Console.WriteLine(e.Message);
}
```

```vb
Try
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _
        "    <Contact>" & vbCrLf & _
        "        <Name>Jim Wilson</Name>" & vbCrLf & _
        "    </Contact>" & vbCrLf & _
        "</Contcts>")

    Console.WriteLine(contacts)
Catch e As System.Xml.XmlException
    Console.WriteLine(e.Message)
End Try
```

由於不正確結束標記 `</Contcts>` ，此範例會擲回下列例外狀況：

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

如需、、和方法擲回之例外狀況的詳細資訊 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> ，請 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 參閱 <xref:System.Xml.XmlReader> 檔。

## <a name="see-also"></a>另請參閱

- [如何剖析字串](parse-string.md)
