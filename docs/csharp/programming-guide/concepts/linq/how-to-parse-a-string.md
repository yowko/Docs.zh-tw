---
title: 如何剖析字串（C#）
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345803"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="c67f7-102">如何剖析字串（C#）</span><span class="sxs-lookup"><span data-stu-id="c67f7-102">How to parse a string (C#)</span></span>

<span data-ttu-id="c67f7-103">本主題示範如何剖析字串以便在 C# 中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="c67f7-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="c67f7-104">範例</span><span class="sxs-lookup"><span data-stu-id="c67f7-104">Example</span></span>

<span data-ttu-id="c67f7-105">下列C#程式碼顯示如何剖析 XML 字串：</span><span class="sxs-lookup"><span data-stu-id="c67f7-105">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="c67f7-106">根 `Contacts` 節點有兩個 `Contact` 節點。</span><span class="sxs-lookup"><span data-stu-id="c67f7-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="c67f7-107">若要存取已剖析 XML 中的某些特定資料，請使用[system.xml.linq.xelement> （）](xref:System.Xml.Linq.XContainer.Elements)方法，在此情況下會傳回根 `Contacts` 節點的子項目。</span><span class="sxs-lookup"><span data-stu-id="c67f7-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="c67f7-108">下列範例會將第一個 `Contact` 節點列印至主控台：</span><span class="sxs-lookup"><span data-stu-id="c67f7-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="c67f7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c67f7-109">See also</span></span>

- [<span data-ttu-id="c67f7-110">如何尋找具有特定屬性（C#）的元素</span><span class="sxs-lookup"><span data-stu-id="c67f7-110">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)
