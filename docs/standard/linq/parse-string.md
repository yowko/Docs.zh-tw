---
title: 如何剖析字串-LINQ to XML
description: '您可以使用 System.xml.linq.xelement> 剖析字串，以 c # 和 Visual Basic 來建立 XML 樹狀結構，而且您可以在 Visual Basic 中建立 xml 常值的 XML 樹狀結構。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: f4bd22acbf3b11d801c791cc591d882810450fd4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552158"
---
# <a name="how-to-parse-a-string-linq-to-xml"></a><span data-ttu-id="6f3c1-103">如何剖析字串 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="6f3c1-103">How to parse a string (LINQ to XML)</span></span>

<span data-ttu-id="6f3c1-104">本文說明如何使用 c # 和 Visual Basic 來剖析字串以建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="6f3c1-104">This article shows how to parse a string to create an XML tree in C# and in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="6f3c1-105">範例</span><span class="sxs-lookup"><span data-stu-id="6f3c1-105">Example</span></span>

<span data-ttu-id="6f3c1-106">下列 c # 程式碼說明如何剖析 XML 字串：</span><span class="sxs-lookup"><span data-stu-id="6f3c1-106">The following C# code shows how to parse an XML string:</span></span>

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

<span data-ttu-id="6f3c1-107">您可以用類似的方式剖析 Visual Basic 中的字串。</span><span class="sxs-lookup"><span data-stu-id="6f3c1-107">You can parse a string in Visual Basic in a similar manner.</span></span> <span data-ttu-id="6f3c1-108">不過，使用 XML 常值會更有效率，如下列程式碼所示，因為 XML 常值不會因為從字串剖析 XML 而受到相同的效能負面影響。</span><span class="sxs-lookup"><span data-stu-id="6f3c1-108">However, it's more efficient to use XML literals, as shown in following code, because XML literals don't suffer from the same performance penalties as parsing XML from a string.</span></span>

<span data-ttu-id="6f3c1-109">藉由使用 XML 常值，您只要將 XML 複製並貼入 Visual Basic 程式中即可。</span><span class="sxs-lookup"><span data-stu-id="6f3c1-109">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>

> [!NOTE]
> <span data-ttu-id="6f3c1-110">從文字檔剖析文字或載入 XML 文件比功能結構沒有效率。</span><span class="sxs-lookup"><span data-stu-id="6f3c1-110">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="6f3c1-111">如果您要從程式碼初始化 XML 樹狀結構，使用功能結構的處理器時間會比剖析文字少。</span><span class="sxs-lookup"><span data-stu-id="6f3c1-111">If you're initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>

```vb
Dim contacts as XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="home">206-555-0144</Phone>
            <Phone Type="work">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type="mobile">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>
```

<span data-ttu-id="6f3c1-112">根 `Contacts` 節點有兩個 `Contact` 節點。</span><span class="sxs-lookup"><span data-stu-id="6f3c1-112">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="6f3c1-113">若要存取剖析的 XML 中的某些特定資料，請使用 [system.xml.linq.xelement> # B1 方法 ( # B1 ](xref:System.Xml.Linq.XContainer.Elements) 方法，在此情況下會傳回根節點的子項目 `Contacts` 。</span><span class="sxs-lookup"><span data-stu-id="6f3c1-113">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="6f3c1-114">下列範例會將第一個 `Contact` 節點列印到主控台：</span><span class="sxs-lookup"><span data-stu-id="6f3c1-114">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

```vb
Dim contactNodes As List(Of XElement) = contacts.Elements("Contact").ToList()
Console.WriteLine(contactNodes(0))
```

## <a name="see-also"></a><span data-ttu-id="6f3c1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f3c1-115">See also</span></span>

- [<span data-ttu-id="6f3c1-116">如何尋找具有特定屬性的項目</span><span class="sxs-lookup"><span data-stu-id="6f3c1-116">How to find an element with a specific attribute</span></span>](find-element-specific-attribute.md)
