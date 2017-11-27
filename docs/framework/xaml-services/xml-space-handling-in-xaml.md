---
title: "XAML 中的 xml:space 處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a5048cbad1d2ea914d041ac3c87a43223b208c3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="c07ee-102">XAML 中的 xml:space 處理</span><span class="sxs-lookup"><span data-stu-id="c07ee-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="c07ee-103">`xml:space`屬性是宣告的空白字元處理行為物件項目內的 XML 定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="c07ee-103">The `xml:space` attribute is an XML-defined attribute that declares the significant whitespace processing behavior within an object element.</span></span> <span data-ttu-id="c07ee-104">這個行為會與相關的項目內所包含的所有內容 （內部文字） 其中`xml:space`宣告，因此也會設定至子元素。</span><span class="sxs-lookup"><span data-stu-id="c07ee-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c07ee-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="c07ee-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="c07ee-106">\-或-</span><span class="sxs-lookup"><span data-stu-id="c07ee-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="c07ee-107">備註</span><span class="sxs-lookup"><span data-stu-id="c07ee-107">Remarks</span></span>  
 <span data-ttu-id="c07ee-108">定義`xml:space`XAML 包括兩個可能的值中的屬性衍生自`xml:space`W3C XML 規格所定義為 「 特殊屬性 」。</span><span class="sxs-lookup"><span data-stu-id="c07ee-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="c07ee-109">預設值`xml:space`屬性是常值`"default"`。</span><span class="sxs-lookup"><span data-stu-id="c07ee-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="c07ee-110">值`"default"`，或如果`xml:space`並未顯示，空白字元剖析的行為是預設的處理，本主題中所定義[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="c07ee-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant whitespace parsing is the default handling, as defined in the topic [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="c07ee-111">若要保留物件元素內容內的空白字元，請指定`xml:space="preserve"`該物件項目。</span><span class="sxs-lookup"><span data-stu-id="c07ee-111">To preserve whitespace within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="c07ee-112">在大部分的方式解讀`xml:space`屬性效果和屬性的值的範圍限於子項目。</span><span class="sxs-lookup"><span data-stu-id="c07ee-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="c07ee-113">如需 XAML 中處理空白字元的完整討論，請參閱[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="c07ee-113">For a complete discussion of whitespace processing in XAML, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07ee-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c07ee-114">See Also</span></span>  
 [<span data-ttu-id="c07ee-115">XAML 中的泛空白字元處理</span><span class="sxs-lookup"><span data-stu-id="c07ee-115">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [<span data-ttu-id="c07ee-116">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="c07ee-116">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
