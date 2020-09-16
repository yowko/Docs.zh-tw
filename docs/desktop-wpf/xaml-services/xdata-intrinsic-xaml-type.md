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
ms.openlocfilehash: d78c2fd63192dc499b119e5b038b92555511a695
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544800"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="00938-102">x:XData 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="00938-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="00938-103">在 XAML 生產環境中啟用 XML 資料島的放置。</span><span class="sxs-lookup"><span data-stu-id="00938-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="00938-104">`x:XData`XAML 處理器不應將內的 XML 專案視為作用中預設 xaml 命名空間或任何其他 XAML 命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="00938-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="00938-105">`x:XData` 可以包含任何格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="00938-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="00938-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="00938-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="00938-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="00938-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="00938-108">封閉資料島的單一根項目。</span><span class="sxs-lookup"><span data-stu-id="00938-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="00938-109">對於大部分的最終取用者而言，沒有單一根的 XML 會視為無效。</span><span class="sxs-lookup"><span data-stu-id="00938-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="00938-110">特別是，如果 `x:XData` 是要做為 WPF 的 xml 資料來源，或許多其他使用 xml 來源進行資料系結的技術，則需要單一根。</span><span class="sxs-lookup"><span data-stu-id="00938-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="00938-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="00938-111">Optional.</span></span> <span data-ttu-id="00938-112">表示 XML 資料的 XML。</span><span class="sxs-lookup"><span data-stu-id="00938-112">XML that represents the XML data.</span></span> <span data-ttu-id="00938-113">任何數目的專案都可以包含為專案資料，而可包含在其他專案中的多個元素：但是，XML 的一般規則也適用。</span><span class="sxs-lookup"><span data-stu-id="00938-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00938-114">備註</span><span class="sxs-lookup"><span data-stu-id="00938-114">Remarks</span></span>

<span data-ttu-id="00938-115">物件內的 XML 元素 `x:XData` 可以重新宣告資料中包含 XMLDOM 的所有可能命名空間和前置詞。</span><span class="sxs-lookup"><span data-stu-id="00938-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="00938-116">`x:XData`.NET XAML 服務可以透過類別，以程式設計方式存取 XML 資料和內建 XAML 類型 <xref:System.Windows.Markup.XData> 。</span><span class="sxs-lookup"><span data-stu-id="00938-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="00938-117">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="00938-117">WPF Usage Notes</span></span>

<span data-ttu-id="00938-118">`x:XData`物件主要是做為的子物件 <xref:System.Windows.Data.XmlDataProvider> ，或者當做 XAML 中屬性 (的子物件， <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> 通常是以屬性專案語法) 表示。</span><span class="sxs-lookup"><span data-stu-id="00938-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="00938-119">資料通常應該會將資料島內的基底 XML 命名空間重新定義為新的預設 XML 命名空間， (設定為空的字串) 。</span><span class="sxs-lookup"><span data-stu-id="00938-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="00938-120">這是簡單資料島最簡單的方式，因為 <xref:System.Windows.Data.Binding.XPath%2A> 用來參考和系結至資料的運算式可以避免包含前置詞。</span><span class="sxs-lookup"><span data-stu-id="00938-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="00938-121">更複雜的資料島可能會定義資料的多個前置詞，並在根目錄上使用 XML 命名空間的特定前置詞。</span><span class="sxs-lookup"><span data-stu-id="00938-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="00938-122">在此情況下，所有 <xref:System.Windows.Data.Binding.XPath%2A> 運算式參考都應該包含適當的命名空間對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="00938-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="00938-123">如需詳細資訊，請參閱資料系結 [總覽](../data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="00938-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="00938-124">技術上來說， `x:XData` 可以當做型別的任何屬性內容使用 <xref:System.Xml.Serialization.IXmlSerializable> 。</span><span class="sxs-lookup"><span data-stu-id="00938-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="00938-125">不過， <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> 這是唯一的主要執行。</span><span class="sxs-lookup"><span data-stu-id="00938-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="00938-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00938-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="00938-127">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="00938-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="00938-128">Binding 標記延伸</span><span class="sxs-lookup"><span data-stu-id="00938-128">Binding Markup Extension</span></span>](/dotnet/desktop/wpf/advanced/binding-markup-extension)
