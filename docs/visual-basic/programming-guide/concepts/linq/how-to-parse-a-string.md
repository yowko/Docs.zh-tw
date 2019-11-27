---
title: 如何：剖析字串
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 31bae00eb3ebf0d8e64fc657693e8c0767c4f5d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344490"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="5b6c0-102">如何：剖析字串（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5b6c0-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="5b6c0-103">本主題說明如何在中C#建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="5b6c0-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b6c0-104">範例</span><span class="sxs-lookup"><span data-stu-id="5b6c0-104">Example</span></span>  
 <span data-ttu-id="5b6c0-105">您可以使用 `XElement.Parse` 方法來剖析 Visual Basic 中的字串。</span><span class="sxs-lookup"><span data-stu-id="5b6c0-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="5b6c0-106">不過，使用 XML 常值會更有效率（如下列程式碼所示），因為 XML 常值在從字串剖析 XML 時，不會受到相同的效能損失。</span><span class="sxs-lookup"><span data-stu-id="5b6c0-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="5b6c0-107">藉由使用 XML 常值，您可以直接將 XML 複製並貼到 Visual Basic 程式中。</span><span class="sxs-lookup"><span data-stu-id="5b6c0-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b6c0-108">從文字檔剖析文字或載入 XML 文件比功能結構沒有效率。</span><span class="sxs-lookup"><span data-stu-id="5b6c0-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="5b6c0-109">如果您要從程式碼初始化 XML 樹狀，使用功能結構比剖析文字所花的處理器時間少。</span><span class="sxs-lookup"><span data-stu-id="5b6c0-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b6c0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b6c0-110">See also</span></span>

- [<span data-ttu-id="5b6c0-111">剖析 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5b6c0-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
