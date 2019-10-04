---
title: HOW TO：剖析字串 (C#)
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 16310e37afec950c372c7b47637986bb0eb399b8
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956614"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="3b8b1-102">HOW TO：剖析字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8b1-102">How to: Parse a String (C#)</span></span>

<span data-ttu-id="3b8b1-103">本主題示範如何剖析字串以便在 C# 中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="3b8b1-104">範例</span><span class="sxs-lookup"><span data-stu-id="3b8b1-104">Example</span></span>

<span data-ttu-id="3b8b1-105">下列C#程式碼顯示如何剖析 XML 字串：</span><span class="sxs-lookup"><span data-stu-id="3b8b1-105">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="3b8b1-106">根 `Contacts` 節點有兩個 @no__t 1 節點。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="3b8b1-107">若要存取已剖析 XML 中的某些特定資料，請使用[system.xml.linq.xelement> （）](xref:System.Xml.Linq.XContainer.Elements)方法，在此情況下會傳回根 `Contacts` 節點的子項目。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="3b8b1-108">下列範例會將第一個 `Contact` 節點列印到主控台：</span><span class="sxs-lookup"><span data-stu-id="3b8b1-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="3b8b1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b8b1-109">See also</span></span>

- [<span data-ttu-id="3b8b1-110">如何：尋找具有特定屬性的項目 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8b1-110">How to: Find an Element with a Specific Attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)
