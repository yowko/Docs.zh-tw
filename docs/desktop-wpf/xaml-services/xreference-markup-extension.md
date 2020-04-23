---
title: x:Reference 標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071378"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="721d5-102">x:Reference 標記延伸</span><span class="sxs-lookup"><span data-stu-id="721d5-102">x:Reference Markup Extension</span></span>

<span data-ttu-id="721d5-103">引用在 XAML 標籤中其他位置聲明的實例。</span><span class="sxs-lookup"><span data-stu-id="721d5-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="721d5-104">參考參考元素的`x:Name`。</span><span class="sxs-lookup"><span data-stu-id="721d5-104">The reference refers to an element's `x:Name`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="721d5-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="721d5-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="721d5-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="721d5-106">XAML Object Element Usage</span></span>

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="721d5-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="721d5-107">XAML Values</span></span>

|||
|-|-|
|`instancexName`|<span data-ttu-id="721d5-108">引用`x:Name`實體的值(或<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-標識屬性的值)。</span><span class="sxs-lookup"><span data-stu-id="721d5-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|

## <a name="remarks"></a><span data-ttu-id="721d5-109">備註</span><span class="sxs-lookup"><span data-stu-id="721d5-109">Remarks</span></span>

<span data-ttu-id="721d5-110">`x:Reference`為元素引用概念提供 XAML 語言級別支援,該概念在 WPF 等特定框架中以其他方式實現。</span><span class="sxs-lookup"><span data-stu-id="721d5-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>

## <a name="xreference-and-wpf"></a><span data-ttu-id="721d5-111">x:參考和WPF</span><span class="sxs-lookup"><span data-stu-id="721d5-111">x:Reference and WPF</span></span>

<span data-ttu-id="721d5-112">在 WPF 和 XAML 2006 中,元素<xref:System.Windows.Data.Binding.ElementName%2A>引用由綁定的框架 級功能解決。</span><span class="sxs-lookup"><span data-stu-id="721d5-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="721d5-113">對於大多數 WPF 應用程式和<xref:System.Windows.Data.Binding.ElementName%2A>方案, 仍應使用綁定。</span><span class="sxs-lookup"><span data-stu-id="721d5-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="721d5-114">此一般指南的例外情況可能包括存在數據上下文或其他範圍範圍注意事項,使數據綁定不切實際,並且不涉及標記編譯的情況。</span><span class="sxs-lookup"><span data-stu-id="721d5-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>

<span data-ttu-id="721d5-115">`x:Reference`是在 XAML 2009 中定義的構造。</span><span class="sxs-lookup"><span data-stu-id="721d5-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="721d5-116">在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯 WPF 標記的 XAML。</span><span class="sxs-lookup"><span data-stu-id="721d5-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="721d5-117">編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 語言關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="721d5-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
