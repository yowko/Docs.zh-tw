---
title: XAML 中的 xml:space 處理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458800"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="e110a-102">XAML 中的 xml:space 處理</span><span class="sxs-lookup"><span data-stu-id="e110a-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="e110a-103">`xml:space` 屬性是 XML 定義的屬性，可宣告物件元素內的重要空白字元處理行為。</span><span class="sxs-lookup"><span data-stu-id="e110a-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="e110a-104">這個行為與在宣告 `xml:space` 的元素中包含的所有內容（內部文字）相關，也會將範圍設為子項目。</span><span class="sxs-lookup"><span data-stu-id="e110a-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e110a-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="e110a-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="e110a-106">\-或-</span><span class="sxs-lookup"><span data-stu-id="e110a-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="e110a-107">備註</span><span class="sxs-lookup"><span data-stu-id="e110a-107">Remarks</span></span>  
 <span data-ttu-id="e110a-108">XAML 中 `xml:space` 屬性的定義，包括它的兩個可能值，衍生自 W3C 規格 for XML 定義為「特殊屬性」的 `xml:space`。</span><span class="sxs-lookup"><span data-stu-id="e110a-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="e110a-109">`xml:space` 屬性的預設值是 `"default"`的常值。</span><span class="sxs-lookup"><span data-stu-id="e110a-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="e110a-110">對於 `"default"`的值，或如果沒有指定 `xml:space`，則重大空白字元剖析的行為是預設處理，如[XAML 中的空白字元處理](whitespace-processing-in-xaml.md)主題中所定義。</span><span class="sxs-lookup"><span data-stu-id="e110a-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="e110a-111">若要保留物件專案內容中的空白字元，請在該物件元素上指定 `xml:space="preserve"`。</span><span class="sxs-lookup"><span data-stu-id="e110a-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="e110a-112">在大部分的解讀之下，`xml:space` 屬性效果和屬性的值都是以子項目為範圍。</span><span class="sxs-lookup"><span data-stu-id="e110a-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="e110a-113">如需 XAML 中空白字元處理的完整討論，請參閱[xaml 中](whitespace-processing-in-xaml.md)的空白字元處理。</span><span class="sxs-lookup"><span data-stu-id="e110a-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e110a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e110a-114">See also</span></span>

- [<span data-ttu-id="e110a-115">XAML 中的空白字元處理</span><span class="sxs-lookup"><span data-stu-id="e110a-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="e110a-116">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="e110a-116">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
