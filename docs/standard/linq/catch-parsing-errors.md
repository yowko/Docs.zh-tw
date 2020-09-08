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
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a><span data-ttu-id="b0cfb-104">如何 (LINQ to XML 中攔截剖析錯誤) </span><span class="sxs-lookup"><span data-stu-id="b0cfb-104">How to catch parsing errors (LINQ to XML)</span></span>

<span data-ttu-id="b0cfb-105">本文說明如何在 c # 或 Visual Basic 中偵測格式錯誤或不正確 XML。</span><span class="sxs-lookup"><span data-stu-id="b0cfb-105">This article shows how to detect badly formed or invalid XML in C# or Visual Basic.</span></span>

<span data-ttu-id="b0cfb-106">LINQ to XML 是使用來執行 <xref:System.Xml.XmlReader> 。</span><span class="sxs-lookup"><span data-stu-id="b0cfb-106">LINQ to XML is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="b0cfb-107">如果將格式不正確或不正確 XML 傳遞給 LINQ to XML，基礎 <xref:System.Xml.XmlReader> 類別將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0cfb-107">If badly formed or invalid XML is passed to LINQ to XML, the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="b0cfb-108">剖析 XML 的各種方法（例如 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> ）不會攔截例外狀況; 然後，您的應用程式就可以攔截到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0cfb-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, don't catch the exception; the exception can then be caught by your application.</span></span>

## <a name="example-parse-invalid-xml"></a><span data-ttu-id="b0cfb-109">範例：剖析不正確 XML</span><span class="sxs-lookup"><span data-stu-id="b0cfb-109">Example: Parse invalid XML</span></span>

<span data-ttu-id="b0cfb-110">下列程式碼會嘗試剖析不正確 XML。</span><span class="sxs-lookup"><span data-stu-id="b0cfb-110">The following code tries to parse invalid XML.</span></span>

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

<span data-ttu-id="b0cfb-111">由於不正確結束標記 `</Contcts>` ，此範例會擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b0cfb-111">Because of the invalid end tag `</Contcts>`, the example throws the following exception:</span></span>

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

<span data-ttu-id="b0cfb-112">如需、、和方法擲回之例外狀況的詳細資訊 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> ，請 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 參閱 <xref:System.Xml.XmlReader> 檔。</span><span class="sxs-lookup"><span data-stu-id="b0cfb-112">For information about the exceptions that the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0cfb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0cfb-113">See also</span></span>

- [<span data-ttu-id="b0cfb-114">如何剖析字串</span><span class="sxs-lookup"><span data-stu-id="b0cfb-114">How to parse a string</span></span>](parse-string.md)
