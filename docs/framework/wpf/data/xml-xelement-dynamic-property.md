---
title: Xml (XElement 動態屬性)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Xml
ms.openlocfilehash: 9bac9797f397a0bea1dda36bf864f88293061893
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920717"
---
# <a name="xml-xelement-dynamic-property"></a><span data-ttu-id="62479-102">Xml (XElement 動態屬性)</span><span class="sxs-lookup"><span data-stu-id="62479-102">Xml (XElement dynamic property)</span></span>

<span data-ttu-id="62479-103">取得項目未格式化的 XML 內容。</span><span class="sxs-lookup"><span data-stu-id="62479-103">Gets the unformatted XML content of the element.</span></span>

## <a name="syntax"></a><span data-ttu-id="62479-104">語法</span><span class="sxs-lookup"><span data-stu-id="62479-104">Syntax</span></span>

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="62479-105">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="62479-105">Property value/return value</span></span>

<span data-ttu-id="62479-106">表示項目未格式化 XML 內容的 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="62479-106">A <xref:System.String> that represents the unformatted XML content of the element.</span></span>

## <a name="remarks"></a><span data-ttu-id="62479-107">備註</span><span class="sxs-lookup"><span data-stu-id="62479-107">Remarks</span></span>

<span data-ttu-id="62479-108">這個屬性等同於 <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> 類別的 <xref:System.Xml.Linq.XNode?displayProperty=fullName> 方法，且 `SaveOptions` 參數設定為 <xref:System.Xml.Linq.SaveOptions>。</span><span class="sxs-lookup"><span data-stu-id="62479-108">This property is equivalent to the <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> method of the <xref:System.Xml.Linq.XNode?displayProperty=fullName> class, with the `SaveOptions` parameter set to <xref:System.Xml.Linq.SaveOptions>.</span></span>

## <a name="see-also"></a><span data-ttu-id="62479-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="62479-109">See also</span></span>

- [<span data-ttu-id="62479-110">XElement 類別動態屬性</span><span class="sxs-lookup"><span data-stu-id="62479-110">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="62479-111">值</span><span class="sxs-lookup"><span data-stu-id="62479-111">Value</span></span>](value-xelement-dynamic-property.md)
