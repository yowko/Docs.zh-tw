---
title: HOW TO：剖析字串 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 513a82cbed796be42eb8e531ec71221ef0ac267f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652445"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="07319-102">HOW TO：剖析字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07319-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="07319-103">本主題說明如何建立 XML 樹狀結構中的C#。</span><span class="sxs-lookup"><span data-stu-id="07319-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07319-104">範例</span><span class="sxs-lookup"><span data-stu-id="07319-104">Example</span></span>  
 <span data-ttu-id="07319-105">您可以使用來剖析字串，以在 Visual Basic 中的`XElement.Parse`方法。</span><span class="sxs-lookup"><span data-stu-id="07319-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="07319-106">不過，它是使用 XML 常值，如下列程式碼所示，因為 XML 常值不會發生相同的效能低落，做為從字串剖析 XML 更有效率。</span><span class="sxs-lookup"><span data-stu-id="07319-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="07319-107">藉由使用 XML 常值，您可以只複製，並將您的 XML 貼到您的 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="07319-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07319-108">從文字檔剖析文字或載入 XML 文件比功能結構沒有效率。</span><span class="sxs-lookup"><span data-stu-id="07319-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="07319-109">如果您要從程式碼初始化 XML 樹狀，使用功能結構比剖析文字所花的處理器時間少。</span><span class="sxs-lookup"><span data-stu-id="07319-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07319-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07319-110">See also</span></span>
- [<span data-ttu-id="07319-111">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07319-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
