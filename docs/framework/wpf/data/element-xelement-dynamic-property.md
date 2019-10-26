---
title: Element (XElement 動態屬性)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.openlocfilehash: fc0277d0dc38574696f01e6915e5382744345771
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920892"
---
# <a name="element-xelement-dynamic-property"></a><span data-ttu-id="0c877-102">Element (XElement 動態屬性)</span><span class="sxs-lookup"><span data-stu-id="0c877-102">Element (XElement dynamic property)</span></span>

<span data-ttu-id="0c877-103">取得用於擷取對應於指定擴充名稱之子項目執行個體的索引子 (Indexer)。</span><span class="sxs-lookup"><span data-stu-id="0c877-103">Gets an indexer used to retrieve the child element instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c877-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c877-104">Syntax</span></span>

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="0c877-105">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="0c877-105">Property value/return value</span></span>

<span data-ttu-id="0c877-106">`XElement Item(String expandedName)` 型別的索引子。</span><span class="sxs-lookup"><span data-stu-id="0c877-106">An indexer of the type `XElement Item(String expandedName)`.</span></span> <span data-ttu-id="0c877-107">如果沒有具有指定之名稱的項目，這個索引子會採用擴充名稱參數，並傳回對應的 <xref:System.Xml.Linq.XElement> 或 `null`。</span><span class="sxs-lookup"><span data-stu-id="0c877-107">This indexer takes an expanded name parameter and returns the corresponding <xref:System.Xml.Linq.XElement>, or `null` if there is no element with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c877-108">備註</span><span class="sxs-lookup"><span data-stu-id="0c877-108">Remarks</span></span>

<span data-ttu-id="0c877-109">這個屬性等同於 <xref:System.Xml.Linq.XContainer.Element%2A> 類別的 <xref:System.Xml.Linq.XContainer?displayProperty=fullName> 方法。</span><span class="sxs-lookup"><span data-stu-id="0c877-109">This property is equivalent to <xref:System.Xml.Linq.XContainer.Element%2A> method of the <xref:System.Xml.Linq.XContainer?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c877-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c877-110">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [<span data-ttu-id="0c877-111">XElement 類別動態屬性</span><span class="sxs-lookup"><span data-stu-id="0c877-111">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="0c877-112">項目</span><span class="sxs-lookup"><span data-stu-id="0c877-112">Elements</span></span>](elements-xelement-dynamic-property.md)
