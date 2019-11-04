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
ms.openlocfilehash: 8496e7c87cf7e6eea996ca7af4f288b7495c7661
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459908"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="c8d35-102">x:XData 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="c8d35-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="c8d35-103">在 XAML 生產環境中啟用 XML 資料島的位置。</span><span class="sxs-lookup"><span data-stu-id="c8d35-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="c8d35-104">XAML 處理器不應處理 `x:XData` 中的 XML 專案，就像它們是作用中的預設 XAML 命名空間或任何其他 XAML 命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="c8d35-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="c8d35-105">`x:XData` 可以包含任何語式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="c8d35-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c8d35-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="c8d35-106">XAML Object Element Usage</span></span>  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c8d35-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="c8d35-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="c8d35-108">括住之資料島的單一根項目。</span><span class="sxs-lookup"><span data-stu-id="c8d35-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="c8d35-109">對於大部分的最終取用者而言，沒有單一根目錄的 XML 會被視為無效。</span><span class="sxs-lookup"><span data-stu-id="c8d35-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="c8d35-110">特別是，如果 `x:XData` 要做為 WPF 的 XML 資料來源，或許多其他使用 XML 來源進行資料系結的技術，則需要單一根目錄。</span><span class="sxs-lookup"><span data-stu-id="c8d35-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="c8d35-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c8d35-111">Optional.</span></span> <span data-ttu-id="c8d35-112">代表 XML 資料的 XML。</span><span class="sxs-lookup"><span data-stu-id="c8d35-112">XML that represents the XML data.</span></span> <span data-ttu-id="c8d35-113">專案資料可以包含任意數目的專案，而嵌套的元素可以包含在其他元素中;不過，XML 的一般規則也適用。</span><span class="sxs-lookup"><span data-stu-id="c8d35-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8d35-114">備註</span><span class="sxs-lookup"><span data-stu-id="c8d35-114">Remarks</span></span>  
 <span data-ttu-id="c8d35-115">`x:XData` 物件內的 XML 元素可以重新宣告資料中包含 XMLDOM 的所有可能的命名空間和前置詞。</span><span class="sxs-lookup"><span data-stu-id="c8d35-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="c8d35-116">透過 <xref:System.Windows.Markup.XData> 類別，可以在 .NET Framework XAML 服務中，以程式設計方式存取 XML 資料和 `x:XData` 內建 XAML 類型。</span><span class="sxs-lookup"><span data-stu-id="c8d35-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="c8d35-117">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="c8d35-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="c8d35-118">`x:XData` 物件主要是做為 <xref:System.Windows.Data.XmlDataProvider>的子物件，或做為 <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> 屬性的子物件（在 XAML 中，這通常是以屬性元素語法表示）。</span><span class="sxs-lookup"><span data-stu-id="c8d35-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="c8d35-119">資料通常應重新定義資料島中的基底 XML 命名空間，以成為新的預設 XML 命名空間（設為空字串）。</span><span class="sxs-lookup"><span data-stu-id="c8d35-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="c8d35-120">這對簡單的資料島而言是最簡單的，因為用來參考和系結資料的 <xref:System.Windows.Data.Binding.XPath%2A> 運算式可以避免包含前置詞。</span><span class="sxs-lookup"><span data-stu-id="c8d35-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="c8d35-121">較複雜的資料島可能會為資料定義多個前置詞，並在根的 XML 命名空間中使用特定的首碼。</span><span class="sxs-lookup"><span data-stu-id="c8d35-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="c8d35-122">在此情況下，所有 <xref:System.Windows.Data.Binding.XPath%2A> 運算式參考都應該包含適當的命名空間對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="c8d35-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="c8d35-123">如需詳細資訊，請參閱 [資料繫結概觀](../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c8d35-123">For more information, see [Data Binding Overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="c8d35-124">就技術上而言，`x:XData` 可以做為 <xref:System.Xml.Serialization.IXmlSerializable>類型之任何屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="c8d35-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="c8d35-125">不過，<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> 是唯一的主要實現。</span><span class="sxs-lookup"><span data-stu-id="c8d35-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d35-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8d35-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="c8d35-127">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="c8d35-127">Data Binding Overview</span></span>](../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c8d35-128">Binding 標記延伸</span><span class="sxs-lookup"><span data-stu-id="c8d35-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
