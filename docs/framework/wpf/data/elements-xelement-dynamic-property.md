---
title: Elements (XElement 動態屬性)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.openlocfilehash: 812adabd3bfb01fd9313ce3f35e6cb0a5e23344e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920850"
---
# <a name="elements-xelement-dynamic-property"></a><span data-ttu-id="4f2d6-102">Elements (XElement 動態屬性)</span><span class="sxs-lookup"><span data-stu-id="4f2d6-102">Elements (XElement dynamic property)</span></span>

<span data-ttu-id="4f2d6-103">取得用於擷取目前項目 (符合指定的擴充名稱) 之子項目的索引子 (Indexer)。</span><span class="sxs-lookup"><span data-stu-id="4f2d6-103">Gets an indexer used to retrieve the child elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="4f2d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f2d6-104">Syntax</span></span>

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="4f2d6-105">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="4f2d6-105">Property value/return value</span></span>

<span data-ttu-id="4f2d6-106">`IEnumerable<XElement> Item(String expandedName)` 型別的索引子。</span><span class="sxs-lookup"><span data-stu-id="4f2d6-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="4f2d6-107">這個索引子會採用所需子項目的擴充名稱，並傳回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中相符的子項目。</span><span class="sxs-lookup"><span data-stu-id="4f2d6-107">This indexer takes the expanded name of the desired child elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="4f2d6-108">備註</span><span class="sxs-lookup"><span data-stu-id="4f2d6-108">Remarks</span></span>

<span data-ttu-id="4f2d6-109">這個屬性等同於 <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XContainer> 方法。</span><span class="sxs-lookup"><span data-stu-id="4f2d6-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="4f2d6-110">傳回集合中的項目順序為 XML 來源文件的順序。</span><span class="sxs-lookup"><span data-stu-id="4f2d6-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="4f2d6-111">這個屬性會使用延後執行。</span><span class="sxs-lookup"><span data-stu-id="4f2d6-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f2d6-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f2d6-112">See also</span></span>

- [<span data-ttu-id="4f2d6-113">XElement 類別動態屬性</span><span class="sxs-lookup"><span data-stu-id="4f2d6-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="4f2d6-114">目</span><span class="sxs-lookup"><span data-stu-id="4f2d6-114">Element</span></span>](element-xelement-dynamic-property.md)
- [<span data-ttu-id="4f2d6-115">子系</span><span class="sxs-lookup"><span data-stu-id="4f2d6-115">Descendants</span></span>](descendants-xelement-dynamic-property.md)
