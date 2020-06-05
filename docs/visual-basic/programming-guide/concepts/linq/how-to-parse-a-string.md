---
title: 作法：剖析字串
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 0a9076fc516bb8e6bc74732ca252fabfeda43d53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398008"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="88ce7-102">如何：剖析字串（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="88ce7-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="88ce7-103">本主題說明如何在 c # 中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="88ce7-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88ce7-104">範例</span><span class="sxs-lookup"><span data-stu-id="88ce7-104">Example</span></span>  
 <span data-ttu-id="88ce7-105">您可以使用方法來剖析 Visual Basic 中的字串 `XElement.Parse` 。</span><span class="sxs-lookup"><span data-stu-id="88ce7-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="88ce7-106">不過，使用 XML 常值更有效率 (如下列程式碼所示)，因為 XML 常值不會和從字串剖析 XML 遭受相同的效能低落。</span><span class="sxs-lookup"><span data-stu-id="88ce7-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="88ce7-107">藉由使用 XML 常值，您可以直接將 XML 複製並貼到 Visual Basic 程式中。</span><span class="sxs-lookup"><span data-stu-id="88ce7-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88ce7-108">從文字檔剖析文字或載入 XML 文件比功能結構沒有效率。</span><span class="sxs-lookup"><span data-stu-id="88ce7-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="88ce7-109">如果您要從程式碼初始化 XML 樹狀，使用功能結構比剖析文字所花的處理器時間少。</span><span class="sxs-lookup"><span data-stu-id="88ce7-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88ce7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88ce7-110">See also</span></span>

- [<span data-ttu-id="88ce7-111">剖析 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="88ce7-111">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
