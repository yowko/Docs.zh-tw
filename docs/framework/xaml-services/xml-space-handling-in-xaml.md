---
title: XAML 中的 xml:space 處理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: d15bab1ad9234959048fa7b7c3fa2bbbeca5fe6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193313"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="4d87b-102">XAML 中的 xml:space 處理</span><span class="sxs-lookup"><span data-stu-id="4d87b-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="4d87b-103">`xml:space`屬性是宣告為物件項目內的顯著泛空白字元處理行為的 XML 定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="4d87b-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="4d87b-104">此行為會與相關的項目內所包含的所有內容 （內部文字） 其中`xml:space`宣告，因此也會設定至子項目。</span><span class="sxs-lookup"><span data-stu-id="4d87b-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4d87b-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="4d87b-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="4d87b-106">\-或-</span><span class="sxs-lookup"><span data-stu-id="4d87b-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="4d87b-107">備註</span><span class="sxs-lookup"><span data-stu-id="4d87b-107">Remarks</span></span>  
 <span data-ttu-id="4d87b-108">定義`xml:space`包括其兩個可能值的 XAML 中的屬性衍生自`xml:space`W3C XML 規格所定義為 「 特殊屬性 」。</span><span class="sxs-lookup"><span data-stu-id="4d87b-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="4d87b-109">預設值`xml:space`屬性是常值`"default"`。</span><span class="sxs-lookup"><span data-stu-id="4d87b-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="4d87b-110">值`"default"`，或者如果`xml:space`並未顯示，行為的顯著泛空白字元剖析為預設處理，主題中所定義[泛空白字元處理中 XAML](whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="4d87b-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="4d87b-111">若要保留物件項目內容中的空白字元，請指定`xml:space="preserve"`該物件元素上。</span><span class="sxs-lookup"><span data-stu-id="4d87b-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="4d87b-112">在大部分的詮釋，`xml:space`屬性效果和屬性的值範圍都限於子項目。</span><span class="sxs-lookup"><span data-stu-id="4d87b-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="4d87b-113">泛空白字元處理在 XAML 中的完整討論，請參閱 <<c0> [ 泛空白字元處理中 XAML](whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="4d87b-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d87b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d87b-114">See also</span></span>

- [<span data-ttu-id="4d87b-115">在 XAML 中處理泛空白字元</span><span class="sxs-lookup"><span data-stu-id="4d87b-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="4d87b-116">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="4d87b-116">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
