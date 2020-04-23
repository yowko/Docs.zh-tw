---
title: XAML 中的 xml:space 處理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071434"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="940b1-102">XAML 中的 xml:space 處理</span><span class="sxs-lookup"><span data-stu-id="940b1-102">xml:space Handling in XAML</span></span>

<span data-ttu-id="940b1-103">該`xml:space`屬性是一個 XML 定義的屬性,用於聲明物件元素中的重要空白處理行為。</span><span class="sxs-lookup"><span data-stu-id="940b1-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="940b1-104">此行為與聲明元素`xml:space`中包含的所有內容(內部文本)以及子元素的範圍相關。</span><span class="sxs-lookup"><span data-stu-id="940b1-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="940b1-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="940b1-105">XAML Attribute Usage</span></span>

```xaml
<object xml:space="preserve" />
```

 <span data-ttu-id="940b1-106">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="940b1-106">\- or -</span></span>

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a><span data-ttu-id="940b1-107">備註</span><span class="sxs-lookup"><span data-stu-id="940b1-107">Remarks</span></span>

<span data-ttu-id="940b1-108">XAML`xml:space`中屬性的定義包括其兩個可能的值,`xml:space`由 W3C XML 規範定義為"特殊屬性"。</span><span class="sxs-lookup"><span data-stu-id="940b1-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>

<span data-ttu-id="940b1-109">屬性的`xml:space`預設值是文字`"default"`值 。</span><span class="sxs-lookup"><span data-stu-id="940b1-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="940b1-110">對於值`"default"`,或者`xml:space`如果 根本不指示,則重要的空白分析行為是預設處理,如[XAML 中的主題白空間處理中](white-space-processing.md)定義的默認處理。</span><span class="sxs-lookup"><span data-stu-id="940b1-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](white-space-processing.md).</span></span>

<span data-ttu-id="940b1-111">要在物件元素內容中保留空白,請在`xml:space="preserve"`該物件元素上指定。</span><span class="sxs-lookup"><span data-stu-id="940b1-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>

<span data-ttu-id="940b1-112">在大多數解釋下,`xml:space`屬性效果和屬性的值範圍限定為子元素。</span><span class="sxs-lookup"><span data-stu-id="940b1-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>

<span data-ttu-id="940b1-113">有關 XAML 中空白處理的完整討論,請參閱[XAML 中的空白處理](white-space-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="940b1-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](white-space-processing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="940b1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="940b1-114">See also</span></span>

- [<span data-ttu-id="940b1-115">XAML 中的空白字元處理</span><span class="sxs-lookup"><span data-stu-id="940b1-115">White-space processing in XAML</span></span>](white-space-processing.md)
- [<span data-ttu-id="940b1-116">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="940b1-116">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
