---
title: "x:XData 內建 XAML 類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
caps.latest.revision: "17"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec46d0363e5b10d3bd3bd3f9c8f4d3694abc1c8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="5a362-102">x:XData 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="5a362-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="5a362-103">可讓在 XAML 生產的 XML 資料島的放置。</span><span class="sxs-lookup"><span data-stu-id="5a362-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="5a362-104">XML 項目內`x:XData`應該不會視為 XAML 處理器來做預設 XAML 命名空間的一部分或任何其他的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="5a362-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="5a362-105">`x:XData`可以包含任意格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="5a362-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="5a362-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="5a362-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5a362-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="5a362-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="5a362-108">括住的資料島的單一根項目。</span><span class="sxs-lookup"><span data-stu-id="5a362-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="5a362-109">大部分的最終取用者，並沒有單一根節點的 XML 會被視為無效。</span><span class="sxs-lookup"><span data-stu-id="5a362-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="5a362-110">特別是，單一根節點時需要`x:XData`適用於 WPF 或許多其他 XML 來源使用資料繫結的技術做為 XML 資料來源。</span><span class="sxs-lookup"><span data-stu-id="5a362-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="5a362-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5a362-111">Optional.</span></span> <span data-ttu-id="5a362-112">代表 XML 資料的 XML。</span><span class="sxs-lookup"><span data-stu-id="5a362-112">XML that represents the XML data.</span></span> <span data-ttu-id="5a362-113">項目資料可包含任意數目的項目和其他項目; 中可包含巢狀項目不過，適用於 XML 的一般規則。</span><span class="sxs-lookup"><span data-stu-id="5a362-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a362-114">備註</span><span class="sxs-lookup"><span data-stu-id="5a362-114">Remarks</span></span>  
 <span data-ttu-id="5a362-115">中的 XML 元素`x:XData`所有可能的命名空間和前置詞的資料中包含的 XMLDOM 物件可以重新宣告。</span><span class="sxs-lookup"><span data-stu-id="5a362-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="5a362-116">以程式設計方式存取 XML 資料和`x:XData`內建 XAML 類型是透過.NET Framework XAML 服務中可能有<xref:System.Windows.Markup.XData>類別。</span><span class="sxs-lookup"><span data-stu-id="5a362-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="5a362-117">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="5a362-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="5a362-118">`x:XData`物件主要是用來當做子物件的<xref:System.Windows.Data.XmlDataProvider>，或或者子物件的<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>屬性 （在 XAML 中，這通常表示在屬性項目語法）。</span><span class="sxs-lookup"><span data-stu-id="5a362-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="5a362-119">資料通常應該重新定義基底資料島是新 （設定為空字串） 的預設 XML 命名空間內的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="5a362-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="5a362-120">這是最簡單的簡單資料島因為<xref:System.Windows.Data.Binding.XPath%2A>用於參考和繫結至資料的運算式可以避免包含的前置詞。</span><span class="sxs-lookup"><span data-stu-id="5a362-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="5a362-121">更複雜的資料島可能定義多個前置詞的資料，並使用特定的前置詞的根目錄中的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="5a362-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="5a362-122">在此情況下，所有<xref:System.Windows.Data.Binding.XPath%2A>運算式參考應包含適當的命名空間對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="5a362-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="5a362-123">如需詳細資訊，請參閱 [資料繫結概觀](../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5a362-123">For more information, see [Data Binding Overview](../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="5a362-124">技術上來說，`x:XData`可用來當做類型的任何屬性的內容<xref:System.Xml.Serialization.IXmlSerializable>。</span><span class="sxs-lookup"><span data-stu-id="5a362-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="5a362-125">不過，<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>是僅提供顯著的實作。</span><span class="sxs-lookup"><span data-stu-id="5a362-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a362-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a362-126">See Also</span></span>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [<span data-ttu-id="5a362-127">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="5a362-127">Data Binding Overview</span></span>](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="5a362-128">Binding 標記延伸</span><span class="sxs-lookup"><span data-stu-id="5a362-128">Binding Markup Extension</span></span>](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
