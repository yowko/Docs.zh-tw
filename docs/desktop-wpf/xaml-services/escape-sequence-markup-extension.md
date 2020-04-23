---
title: '{}逸出序列 - 標記延伸'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071742"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="6e75d-102">{}逸出序列/標記延伸</span><span class="sxs-lookup"><span data-stu-id="6e75d-102">{} Escape sequence / markup extension</span></span>

<span data-ttu-id="6e75d-103">為屬性值提供 XAML 轉義序列。</span><span class="sxs-lookup"><span data-stu-id="6e75d-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="6e75d-104">轉義序列允許將屬性中的後續值解釋為文本。</span><span class="sxs-lookup"><span data-stu-id="6e75d-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="6e75d-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="6e75d-105">XAML Attribute Usage</span></span>

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a><span data-ttu-id="6e75d-106">XAML 屬性項目用法</span><span class="sxs-lookup"><span data-stu-id="6e75d-106">XAML Property Element Usage</span></span>

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="6e75d-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="6e75d-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="6e75d-108">*字面值*</span><span class="sxs-lookup"><span data-stu-id="6e75d-108">*literalValue*</span></span>|<span data-ttu-id="6e75d-109">逸出序列的文字字串。</span><span class="sxs-lookup"><span data-stu-id="6e75d-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="6e75d-110">通常,此字串包含打開或關閉大括弧 (\* 或 |)。</span><span class="sxs-lookup"><span data-stu-id="6e75d-110">Typically this string contains an open or close brace ({ or }).</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e75d-111">備註</span><span class="sxs-lookup"><span data-stu-id="6e75d-111">Remarks</span></span>

<span data-ttu-id="6e75d-112">逸出序列{}( ) 用於讓開啟大括號 (\*) 可用作 XAML 中的字面字元。</span><span class="sxs-lookup"><span data-stu-id="6e75d-112">The escape sequence ({}) is used so that an open brace ({) can be used as a literal character in XAML.</span></span>

<span data-ttu-id="6e75d-113">XAML 讀取器通常使用開放大括弧 (*) 來表示標記擴展的入口點;但是,他們首先檢查下一個字元以確定它是否是右大括弧 (*)。</span><span class="sxs-lookup"><span data-stu-id="6e75d-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="6e75d-114">只有當兩個大括號{}( ) 相鄰時, 它們才被視為轉義序列.</span><span class="sxs-lookup"><span data-stu-id="6e75d-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>

<span data-ttu-id="6e75d-115">如果遇到轉義序列,XAML 讀取器應作為字串處理字串的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="6e75d-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="6e75d-116">但是,如果轉義序列應用於具有類型轉換器的成員,則當 XAML 編寫器解釋該字串時,該字串可能會進行類型轉換。</span><span class="sxs-lookup"><span data-stu-id="6e75d-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>

<span data-ttu-id="6e75d-117">轉義序列不是標記擴展,並且不由類支援。</span><span class="sxs-lookup"><span data-stu-id="6e75d-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="6e75d-118">但是,XAML 讀取器(包括自定義 XAML 讀取器)應遵守的約定。</span><span class="sxs-lookup"><span data-stu-id="6e75d-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>

<span data-ttu-id="6e75d-119">引號 (") 不能以這種方式用作轉義序列。</span><span class="sxs-lookup"><span data-stu-id="6e75d-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="6e75d-120">如果需要將引號設置為非內容屬性的屬性值,請使用屬性元素語法並將引號作為字串放在屬性元素中,或使用 XML 字元實體。</span><span class="sxs-lookup"><span data-stu-id="6e75d-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="6e75d-121">對於內容屬性,引號可以是整個內容。</span><span class="sxs-lookup"><span data-stu-id="6e75d-121">For a content property, the quotation mark can be the entire content.</span></span>

<span data-ttu-id="6e75d-122">指定必須包含命名{}空間限定符的位置的 XML 類型時,經常需要轉義序列 ( ) 。</span><span class="sxs-lookup"><span data-stu-id="6e75d-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="6e75d-123">此位置包括 XAML 屬性值的開頭,以及等於符號 (\*) 之後的標記擴展中。</span><span class="sxs-lookup"><span data-stu-id="6e75d-123">This location includes the start of a XAML attribute value, and in a markup extension immediately after an equal sign (=).</span></span> <span data-ttu-id="6e75d-124">下面的範例顯示出現在 XAML 屬性值開頭的 XML 命名空間的轉義序列。</span><span class="sxs-lookup"><span data-stu-id="6e75d-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a><span data-ttu-id="6e75d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e75d-125">See also</span></span>

- [<span data-ttu-id="6e75d-126">XAML 的類型轉換子和標記延伸</span><span class="sxs-lookup"><span data-stu-id="6e75d-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions.md)
- [<span data-ttu-id="6e75d-127">XML 字元實體和 XAML</span><span class="sxs-lookup"><span data-stu-id="6e75d-127">XML Character Entities and XAML</span></span>](xml-character-entities.md)
