---
title: '{}Escape 序列-標記延伸'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053867"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="aaa60-102">{} 逸出序列/標記延伸</span><span class="sxs-lookup"><span data-stu-id="aaa60-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="aaa60-103">提供屬性值的 XAML 逸出序列。</span><span class="sxs-lookup"><span data-stu-id="aaa60-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="aaa60-104">Escape 序列允許將屬性中的後續值視為常值。</span><span class="sxs-lookup"><span data-stu-id="aaa60-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="aaa60-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="aaa60-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="aaa60-106">XAML 屬性項目用法</span><span class="sxs-lookup"><span data-stu-id="aaa60-106">XAML Property Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="aaa60-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="aaa60-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aaa60-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="aaa60-108">*literalValue*</span></span>|<span data-ttu-id="aaa60-109">在 escape 序列之後的常值字串。</span><span class="sxs-lookup"><span data-stu-id="aaa60-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="aaa60-110">這個字串通常包含左或右大括弧（{或}）。</span><span class="sxs-lookup"><span data-stu-id="aaa60-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaa60-111">備註</span><span class="sxs-lookup"><span data-stu-id="aaa60-111">Remarks</span></span>  
 <span data-ttu-id="aaa60-112">使用 escape 序列（{}），以便在 XAML 中使用左大括弧（{）做為常值字元。</span><span class="sxs-lookup"><span data-stu-id="aaa60-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="aaa60-113">XAML 讀取器通常會使用左括弧（{）來表示標記延伸的進入點; 不過，它們會先檢查下一個字元，以判斷它是否為右大括弧（}）。</span><span class="sxs-lookup"><span data-stu-id="aaa60-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="aaa60-114">只有當兩個大括弧{}（）相鄰時，它們是否視為逸出序列。</span><span class="sxs-lookup"><span data-stu-id="aaa60-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="aaa60-115">如果遇到 escape 序列，XAML 讀取器應該將字串的其餘部分當做字串處理。</span><span class="sxs-lookup"><span data-stu-id="aaa60-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="aaa60-116">不過，如果將 escape 序列套用至具有類型轉換器的成員，則當 XAML 寫入器解讀該字串時，可能會經歷類型轉換。</span><span class="sxs-lookup"><span data-stu-id="aaa60-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="aaa60-117">Escape 序列不是標記延伸，而且不受類別支援。</span><span class="sxs-lookup"><span data-stu-id="aaa60-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="aaa60-118">不過，這是 XAML 讀取器（包括自訂 XAML 讀取器）應遵守的慣例。</span><span class="sxs-lookup"><span data-stu-id="aaa60-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="aaa60-119">不能以這種方式將引號（"）當做 escape 序列使用。</span><span class="sxs-lookup"><span data-stu-id="aaa60-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="aaa60-120">如果您需要將引號設定為 noncontent 屬性的屬性值，請使用屬性專案語法，並將引號放在 property 專案中做為字串，或使用 XML 字元實體。</span><span class="sxs-lookup"><span data-stu-id="aaa60-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="aaa60-121">若為 content 屬性，引號可以是整個內容。</span><span class="sxs-lookup"><span data-stu-id="aaa60-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="aaa60-122">指定必須在 XAML{}標記延伸可能出現之位置中包含命名空間限定詞的 XML 類型時，通常需要使用 escape 序列（）。</span><span class="sxs-lookup"><span data-stu-id="aaa60-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="aaa60-123">這包括 XAML 屬性值的開頭，以及在標記延伸中，緊接在等號（=）之後。</span><span class="sxs-lookup"><span data-stu-id="aaa60-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="aaa60-124">下列範例顯示在 XAML 屬性值開頭出現之 XML 命名空間的逸出序列。</span><span class="sxs-lookup"><span data-stu-id="aaa60-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="aaa60-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaa60-125">See also</span></span>

- [<span data-ttu-id="aaa60-126">XAML 的類型轉換子和標記延伸</span><span class="sxs-lookup"><span data-stu-id="aaa60-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="aaa60-127">XML 字元實體和 XAML</span><span class="sxs-lookup"><span data-stu-id="aaa60-127">XML Character Entities and XAML</span></span>](xml-character-entities-and-xaml.md)
