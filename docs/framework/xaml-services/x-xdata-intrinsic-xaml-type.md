---
title: x:XData 內建 XAML 類型
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: c8044bc341ded6ef7b03bbdf701e724654460d54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125155"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="db5e5-102">x:XData 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="db5e5-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="db5e5-103">可讓 XAML 生產環境內的 XML 資料島的放置。</span><span class="sxs-lookup"><span data-stu-id="db5e5-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="db5e5-104">中的 XML 項目`x:XData`應該不視為 XAML 處理器所處理預設 XAML 命名空間的一部分或任何其他的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="db5e5-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="db5e5-105">`x:XData` 可以包含任意格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="db5e5-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="db5e5-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="db5e5-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="db5e5-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="db5e5-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="db5e5-108">被封入的資料島單一根項目。</span><span class="sxs-lookup"><span data-stu-id="db5e5-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="db5e5-109">大部分的最終取用者，並沒有單一根節點的 XML 視為無效。</span><span class="sxs-lookup"><span data-stu-id="db5e5-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="db5e5-110">特別是，單一根節點如果，則需要`x:XData`適用於 WPF 或許多其他資料繫結使用 XML 來源的技術做為 XML 資料來源。</span><span class="sxs-lookup"><span data-stu-id="db5e5-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="db5e5-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="db5e5-111">Optional.</span></span> <span data-ttu-id="db5e5-112">代表 XML 資料的 XML。</span><span class="sxs-lookup"><span data-stu-id="db5e5-112">XML that represents the XML data.</span></span> <span data-ttu-id="db5e5-113">項目資料可包含任意數目的項目和其他項目; 中可包含巢狀項目不過，套用 XML 的一般規則。</span><span class="sxs-lookup"><span data-stu-id="db5e5-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db5e5-114">備註</span><span class="sxs-lookup"><span data-stu-id="db5e5-114">Remarks</span></span>  
 <span data-ttu-id="db5e5-115">中的 XML 項目`x:XData`所有可能的命名空間和前置詞的資料內包含的 XMLDOM 物件可以重新宣告。</span><span class="sxs-lookup"><span data-stu-id="db5e5-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="db5e5-116">以程式設計方式存取 XML 資料和`x:XData`透過.NET Framework XAML 服務中的內建 XAML 類型可<xref:System.Windows.Markup.XData>類別。</span><span class="sxs-lookup"><span data-stu-id="db5e5-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="db5e5-117">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="db5e5-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="db5e5-118">`x:XData`物件主要是做為子物件<xref:System.Windows.Data.XmlDataProvider>，或者改的子物件<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>屬性 （在 XAML，這通常表示屬性項目語法中）。</span><span class="sxs-lookup"><span data-stu-id="db5e5-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="db5e5-119">資料通常應該重新定義基底資料島是新 （設為空字串） 的預設 XML 命名空間內的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="db5e5-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="db5e5-120">這是最簡單的簡單資料群島，因為<xref:System.Windows.Data.Binding.XPath%2A>用來參考和繫結至資料的運算式可以避免包含的前置詞。</span><span class="sxs-lookup"><span data-stu-id="db5e5-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="db5e5-121">更複雜的資料島可能會定義資料的多個前置詞，並使用 XML 命名空間根目錄的特定前置詞。</span><span class="sxs-lookup"><span data-stu-id="db5e5-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="db5e5-122">在此情況下，所有<xref:System.Windows.Data.Binding.XPath%2A>運算式參考應該包含適當的命名空間對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="db5e5-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="db5e5-123">如需詳細資訊，請參閱 [資料繫結概觀](../wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="db5e5-123">For more information, see [Data Binding Overview](../wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="db5e5-124">技術上來說，`x:XData`可用之類型的任何屬性的內容當做<xref:System.Xml.Serialization.IXmlSerializable>。</span><span class="sxs-lookup"><span data-stu-id="db5e5-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="db5e5-125">不過，<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>是只提供顯著的實作。</span><span class="sxs-lookup"><span data-stu-id="db5e5-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5e5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db5e5-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="db5e5-127">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="db5e5-127">Data Binding Overview</span></span>](../wpf/data/data-binding-overview.md)
- [<span data-ttu-id="db5e5-128">Binding 標記延伸</span><span class="sxs-lookup"><span data-stu-id="db5e5-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
