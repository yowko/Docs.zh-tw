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
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071539"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="4105a-102">x:XData 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="4105a-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="4105a-103">支援在 XAML 生產中放置 XML 資料孤島。</span><span class="sxs-lookup"><span data-stu-id="4105a-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="4105a-104">XAML`x:XData`處理器不應將其中的 XML 元素視為代理預設 XAML 命名空間或任何其他 XAML 命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="4105a-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="4105a-105">`x:XData`可以包含任意格式良好的 XML。</span><span class="sxs-lookup"><span data-stu-id="4105a-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="4105a-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="4105a-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="4105a-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="4105a-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="4105a-108">封閉數據島的單根元素。</span><span class="sxs-lookup"><span data-stu-id="4105a-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="4105a-109">對於大多數最終消費者,沒有單個根的 XML 被視為無效。</span><span class="sxs-lookup"><span data-stu-id="4105a-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="4105a-110">特別是,如果`x:XData`用作 WPF 的 XML 數據源或使用 XML 源進行數據綁定的許多其他技術,則需要單個根。</span><span class="sxs-lookup"><span data-stu-id="4105a-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="4105a-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4105a-111">Optional.</span></span> <span data-ttu-id="4105a-112">表示 XML 資料的 XML。</span><span class="sxs-lookup"><span data-stu-id="4105a-112">XML that represents the XML data.</span></span> <span data-ttu-id="4105a-113">任意數量的元素可以包含在元素數據中,嵌套元素可以包含在其他元素中;但是,XML 的一般規則適用。</span><span class="sxs-lookup"><span data-stu-id="4105a-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4105a-114">備註</span><span class="sxs-lookup"><span data-stu-id="4105a-114">Remarks</span></span>

<span data-ttu-id="4105a-115">`x:XData`物件中的 XML 元素可以重新聲明數據中包含 XMLDOM 的所有可能的命名空間和前綴。</span><span class="sxs-lookup"><span data-stu-id="4105a-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="4105a-116">在 .NET XAML`x:XData`<xref:System.Windows.Markup.XData>服務中可以通過 類對 XML 數據和內在 XAML 類型進行程式設計存取。</span><span class="sxs-lookup"><span data-stu-id="4105a-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="4105a-117">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="4105a-117">WPF Usage Notes</span></span>

<span data-ttu-id="4105a-118">該`x:XData`物件主要用<xref:System.Windows.Data.XmlDataProvider>作 的子物件,或者用作<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>屬性的 子物件(在 XAML 中,這通常用屬性元素語法表示)。</span><span class="sxs-lookup"><span data-stu-id="4105a-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="4105a-119">數據通常應重新定義資料孤島中的基本 XML 命名空間,作為新的預設 XML 命名空間(設置為空字串)。</span><span class="sxs-lookup"><span data-stu-id="4105a-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="4105a-120">對於簡單的數據孤島來說,這很容易,<xref:System.Windows.Data.Binding.XPath%2A>因為用於引用和綁定到數據的表達式可以避免包含首碼。</span><span class="sxs-lookup"><span data-stu-id="4105a-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="4105a-121">更複雜的數據孤島可能為數據定義多個首碼,並使用根目錄的 XML 命名空間的特定首碼。</span><span class="sxs-lookup"><span data-stu-id="4105a-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="4105a-122">在這種情況下,所有<xref:System.Windows.Data.Binding.XPath%2A>表達式引用都應包含適當的命名空間映射前綴。</span><span class="sxs-lookup"><span data-stu-id="4105a-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="4105a-123">有關詳細資訊,請參閱[資料繫結此概述](../data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4105a-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="4105a-124">從技術上講,`x:XData`可用作任何<xref:System.Xml.Serialization.IXmlSerializable>類型 屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="4105a-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="4105a-125">然而,<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>是唯一突出的實現。</span><span class="sxs-lookup"><span data-stu-id="4105a-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="4105a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4105a-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="4105a-127">資料繫結概述</span><span class="sxs-lookup"><span data-stu-id="4105a-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="4105a-128">繫結標記延伸</span><span class="sxs-lookup"><span data-stu-id="4105a-128">Binding Markup Extension</span></span>](../../framework/wpf/advanced/binding-markup-extension.md)
