---
title: x:Reference 標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938875"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="e7c53-102">x:Reference 標記延伸</span><span class="sxs-lookup"><span data-stu-id="e7c53-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="e7c53-103">在 XAML 標記中其他位置宣告的執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="e7c53-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="e7c53-104">參考所參考的項目`x:Name`。</span><span class="sxs-lookup"><span data-stu-id="e7c53-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e7c53-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="e7c53-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="e7c53-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="e7c53-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e7c53-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="e7c53-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="e7c53-108">`x:Name`值 (或值<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-識別屬性) 的參考的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7c53-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7c53-109">備註</span><span class="sxs-lookup"><span data-stu-id="e7c53-109">Remarks</span></span>  
 <span data-ttu-id="e7c53-110">`x:Reference` 否則在特定的架構，例如 WPF 中實作的項目參考概念提供 XAML 語言層級支援。</span><span class="sxs-lookup"><span data-stu-id="e7c53-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="e7c53-111">x： 參考和 WPF</span><span class="sxs-lookup"><span data-stu-id="e7c53-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="e7c53-112">在 WPF 和 XAML 2006 中，項目參考會定址的架構層級功能<xref:System.Windows.Data.Binding.ElementName%2A>繫結。</span><span class="sxs-lookup"><span data-stu-id="e7c53-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="e7c53-113">大部分的 WPF 應用程式和案例，<xref:System.Windows.Data.Binding.ElementName%2A>仍應使用繫結。</span><span class="sxs-lookup"><span data-stu-id="e7c53-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="e7c53-114">這個一般的指導方針的例外狀況可能包含的情況下，有資料內容或其他範圍的考量，讓資料繫結並不實用，而且不進行標記編譯。</span><span class="sxs-lookup"><span data-stu-id="e7c53-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="e7c53-115">`x:Reference` XAML 2009 中定義的建構。</span><span class="sxs-lookup"><span data-stu-id="e7c53-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="e7c53-116">在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯 WPF 標記的 XAML。</span><span class="sxs-lookup"><span data-stu-id="e7c53-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="e7c53-117">編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 語言關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="e7c53-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
