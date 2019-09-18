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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053702"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="fca21-102">x:XData 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="fca21-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="fca21-103">在 XAML 生產環境中啟用 XML 資料島的位置。</span><span class="sxs-lookup"><span data-stu-id="fca21-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="fca21-104">XAML 處理器不`x:XData`應處理內的 XML 專案，如同它們屬於作用中的預設 xaml 命名空間或任何其他 XAML 命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="fca21-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="fca21-105">`x:XData`可以包含任何語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="fca21-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="fca21-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="fca21-106">XAML Object Element Usage</span></span>  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="fca21-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="fca21-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="fca21-108">括住之資料島的單一根項目。</span><span class="sxs-lookup"><span data-stu-id="fca21-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="fca21-109">對於大部分的最終取用者而言，沒有單一根目錄的 XML 會被視為無效。</span><span class="sxs-lookup"><span data-stu-id="fca21-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="fca21-110">特別是，如果`x:XData`要做為 WPF 的 xml 資料來源，或許多其他使用 xml 來源進行資料系結的技術，則需要單一根目錄。</span><span class="sxs-lookup"><span data-stu-id="fca21-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="fca21-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="fca21-111">Optional.</span></span> <span data-ttu-id="fca21-112">代表 XML 資料的 XML。</span><span class="sxs-lookup"><span data-stu-id="fca21-112">XML that represents the XML data.</span></span> <span data-ttu-id="fca21-113">專案資料可以包含任意數目的專案，而嵌套的元素可以包含在其他元素中;不過，XML 的一般規則也適用。</span><span class="sxs-lookup"><span data-stu-id="fca21-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fca21-114">備註</span><span class="sxs-lookup"><span data-stu-id="fca21-114">Remarks</span></span>  
 <span data-ttu-id="fca21-115">`x:XData`物件內的 XML 元素可以重新宣告資料中包含 XMLDOM 的所有可能的命名空間和前置詞。</span><span class="sxs-lookup"><span data-stu-id="fca21-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="fca21-116">以程式設計方式存取 XML 資料`x:XData`和內建 XAML 類型，可以<xref:System.Windows.Markup.XData>透過類別在 .NET Framework XAML 服務中進行。</span><span class="sxs-lookup"><span data-stu-id="fca21-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="fca21-117">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="fca21-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="fca21-118">物件主要是做為的子物件<xref:System.Windows.Data.XmlDataProvider>，或做為<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>屬性的子物件（在 XAML 中，這通常是以屬性元素語法表示）。 `x:XData`</span><span class="sxs-lookup"><span data-stu-id="fca21-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="fca21-119">資料通常應重新定義資料島中的基底 XML 命名空間，以成為新的預設 XML 命名空間（設為空字串）。</span><span class="sxs-lookup"><span data-stu-id="fca21-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="fca21-120">這對於簡單的資料島而言是最<xref:System.Windows.Data.Binding.XPath%2A>簡單的，因為用來參考和系結資料的運算式可以避免包含前置詞。</span><span class="sxs-lookup"><span data-stu-id="fca21-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="fca21-121">較複雜的資料島可能會為資料定義多個前置詞，並在根的 XML 命名空間中使用特定的首碼。</span><span class="sxs-lookup"><span data-stu-id="fca21-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="fca21-122">在此情況下， <xref:System.Windows.Data.Binding.XPath%2A>所有運算式參考都應該包含適當的命名空間對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="fca21-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="fca21-123">如需詳細資訊，請參閱 [資料繫結概觀](../wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="fca21-123">For more information, see [Data Binding Overview](../wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="fca21-124">技術上`x:XData`而言，可以當做類型<xref:System.Xml.Serialization.IXmlSerializable>之任何屬性的內容使用。</span><span class="sxs-lookup"><span data-stu-id="fca21-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="fca21-125">不過， <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>是唯一的主要實現。</span><span class="sxs-lookup"><span data-stu-id="fca21-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca21-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fca21-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="fca21-127">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="fca21-127">Data Binding Overview</span></span>](../wpf/data/data-binding-overview.md)
- [<span data-ttu-id="fca21-128">Binding 標記延伸</span><span class="sxs-lookup"><span data-stu-id="fca21-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
