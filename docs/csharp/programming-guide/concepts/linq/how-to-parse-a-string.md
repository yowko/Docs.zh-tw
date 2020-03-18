---
title: 如何分析字串 （C#）
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345803"
---
# <a name="how-to-parse-a-string-c"></a>如何分析字串 （C#）

本主題示範如何剖析字串以便在 C# 中建立 XML 樹狀結構。

## <a name="example"></a>範例

以下 C# 代碼演示如何解析 XML 字串：

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

根`Contacts`節點有兩個`Contact`節點。 要訪問解析的 XML 中的某些特定資料，請使用[XElement.element（）](xref:System.Xml.Linq.XContainer.Elements)方法，在這種情況下，該方法將返回根`Contacts`節點的子項目。 以下示例將第一個`Contact`節點列印到主控台：

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a>另請參閱

- [如何查找具有特定屬性 （C#） 的元素](how-to-find-an-element-with-a-specific-attribute.md)
