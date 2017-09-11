---
title: "如何：剖析字串 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8aa6e0235a5a9e834167b74897121a1ab003078b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="db048-102">如何：剖析字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="db048-102">How to: Parse a String (C#)</span></span>
<span data-ttu-id="db048-103">本主題示範如何剖析字串以便在 C# 中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="db048-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db048-104">範例</span><span class="sxs-lookup"><span data-stu-id="db048-104">Example</span></span>  
 <span data-ttu-id="db048-105">下列 C# 程式碼顯示如何剖析字串。</span><span class="sxs-lookup"><span data-stu-id="db048-105">The following C# code shows how to parse a string.</span></span>  
  
```csharp  
XElement contacts = XElement.Parse(  
    @"<Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type=""home"">206-555-0144</Phone>  
            <Phone type=""work"">425-555-0145</Phone>  
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
  
## <a name="see-also"></a><span data-ttu-id="db048-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db048-106">See Also</span></span>  
 [<span data-ttu-id="db048-107">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="db048-107">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

