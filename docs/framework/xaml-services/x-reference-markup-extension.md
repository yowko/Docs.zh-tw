---
title: "x:Reference 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 06e59e7686004f8fd44473bd9572ed07a0118d1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="1bd7e-102">x:Reference 標記延伸</span><span class="sxs-lookup"><span data-stu-id="1bd7e-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="1bd7e-103">會參考其他地方在 XAML 標記中宣告執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="1bd7e-104">參考所參考的項目`x:Name`。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1bd7e-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="1bd7e-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="1bd7e-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="1bd7e-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1bd7e-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="1bd7e-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="1bd7e-108">`x:Name`值 (或值<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-識別屬性) 的參考執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd7e-109">備註</span><span class="sxs-lookup"><span data-stu-id="1bd7e-109">Remarks</span></span>  
 <span data-ttu-id="1bd7e-110">`x:Reference`提供的項目參考概念否則實作中特定的架構，例如 WPF XAML 語言層級支援。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="1bd7e-111">X:reference 和 WPF</span><span class="sxs-lookup"><span data-stu-id="1bd7e-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="1bd7e-112">在 WPF 和 XAML 2006 中，項目參考期刊的架構層級功能<xref:System.Windows.Data.Binding.ElementName%2A>繫結。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="1bd7e-113">大部分的 WPF 應用程式和案例，<xref:System.Windows.Data.Binding.ElementName%2A>仍應使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="1bd7e-114">這個一般指引的例外狀況可能包含案例，其中有資料內容或其他範圍考量資料繫結變得不可行，而且不進行標記編譯。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="1bd7e-115">`x:Reference`在 XAML 2009 中定義的建構。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="1bd7e-116">在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯 WPF 標記的 XAML。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="1bd7e-117">編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 語言關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="1bd7e-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
