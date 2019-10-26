---
title: LINQ to XML 動態屬性參考
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: ca3684716f9b562d0e6a006c26730a1d1a28f8b1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920927"
---
# <a name="linq-to-xml-dynamic-properties"></a><span data-ttu-id="4bcc1-102">LINQ to XML 動態屬性</span><span class="sxs-lookup"><span data-stu-id="4bcc1-102">LINQ to XML dynamic properties</span></span>

<span data-ttu-id="4bcc1-103">本節提供 LINQ to XML 之動態屬性的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-103">This section provides reference information about the dynamic properties in LINQ to XML.</span></span> <span data-ttu-id="4bcc1-104">特別是，這些屬性會由 <xref:System.Xml.Linq.XAttribute> 命名空間中的 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq> 類別公開。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-104">Specifically, these properties are exposed by the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, which are in the <xref:System.Xml.Linq> namespace.</span></span>

<span data-ttu-id="4bcc1-105">每個動態屬性都相當於相同類別中的標準公用屬性或方法，如[使用 LINQ to XML 進行 WPF 資料繫結概觀](wpf-data-binding-with-linq-to-xml-overview.md)主題中所述。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-105">As explained in the topic [Overview of WPF data binding with LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), each of the dynamic properties is equivalent to a standard public property or method in the same class.</span></span> <span data-ttu-id="4bcc1-106">大部分的用途應該都可以使用這些標準成員；動態屬性是針對 LINQ to XML 資料繫結案例特別提供。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-106">These standard members should be used for most purposes; dynamic properties are provided specifically for LINQ to XML data binding scenarios.</span></span> <span data-ttu-id="4bcc1-107">如需有關這些類別之標準成員的詳細資訊，請參閱 <xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 參考主題。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-107">For more information about the standard members of these classes, see the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> reference topics.</span></span>

<span data-ttu-id="4bcc1-108">關於其解析的值，本節中的動態屬性分為兩種分類：</span><span class="sxs-lookup"><span data-stu-id="4bcc1-108">With respect to their resolved values, the dynamic properties in this section fall into two categories:</span></span>

- <span data-ttu-id="4bcc1-109">簡單分類，例如，`Value` 和 <xref:System.Xml.Linq.XAttribute> 類別中的 <xref:System.Xml.Linq.XElement> 屬性，可解析為單一的值。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-109">Simple ones, such as the `Value` properties in the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, that resolve to a single value.</span></span>

- <span data-ttu-id="4bcc1-110">索引值 (例如 <xref:System.Xml.Linq.XElement> 的 [Elements](elements-xelement-dynamic-property.md) 和 [Descendants](descendants-xelement-dynamic-property.md) 屬性)，可解析為索引子類型。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-110">Indexed values, such as the [Elements](elements-xelement-dynamic-property.md) and [Descendants](descendants-xelement-dynamic-property.md) properties of <xref:System.Xml.Linq.XElement>, that resolve into an indexer type.</span></span> <span data-ttu-id="4bcc1-111">對於要解析為所需數值或集合的索引子型別，必須將擴充名稱參數傳遞給它們。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-111">For indexer types to be resolved to the desired value or collection, an expanded name parameter must be passed to them.</span></span>

<span data-ttu-id="4bcc1-112">傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型之索引值的所有動態屬性都使用延緩執行。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-112">All the dynamic properties that return an indexed value of type <xref:System.Collections.Generic.IEnumerable%601> use deferred execution.</span></span> <span data-ttu-id="4bcc1-113">如需延後執行的詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)。</span><span class="sxs-lookup"><span data-stu-id="4bcc1-113">For more information about deferred execution, see [Introduction to LINQ queries (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).</span></span>

## <a name="reference"></a><span data-ttu-id="4bcc1-114">參考資料</span><span class="sxs-lookup"><span data-stu-id="4bcc1-114">Reference</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="4bcc1-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="4bcc1-115">See also</span></span>

- [<span data-ttu-id="4bcc1-116">使用 LINQ to XML 進行 WPF 資料繫結</span><span class="sxs-lookup"><span data-stu-id="4bcc1-116">WPF data binding with LINQ to XML</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="4bcc1-117">WPF 資料繫結與 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="4bcc1-117">WPF data binding with LINQ to XML overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="4bcc1-118">LINQ 查詢簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="4bcc1-118">Introduction to LINQ queries (C#)</span></span>](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
