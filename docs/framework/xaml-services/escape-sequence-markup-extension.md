---
title: '{} 逸出序列的標記延伸'
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
ms.openlocfilehash: a90f6928d68eddd29762e6206769dd7f07704e4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564517"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="f7178-102">{} 逸出序列 / 標記延伸</span><span class="sxs-lookup"><span data-stu-id="f7178-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="f7178-103">提供 XAML 逸出序列的屬性值。</span><span class="sxs-lookup"><span data-stu-id="f7178-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="f7178-104">逸出序列必須解譯成常值屬性中讓後續的值。</span><span class="sxs-lookup"><span data-stu-id="f7178-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f7178-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="f7178-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="f7178-106">XAML 屬性項目用法</span><span class="sxs-lookup"><span data-stu-id="f7178-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f7178-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="f7178-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7178-108">*LiteralValue*</span><span class="sxs-lookup"><span data-stu-id="f7178-108">*literalValue*</span></span>|<span data-ttu-id="f7178-109">常值字串的逸出序列。</span><span class="sxs-lookup"><span data-stu-id="f7178-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="f7178-110">這個字串通常包含開啟或關閉括號 （{或}）。</span><span class="sxs-lookup"><span data-stu-id="f7178-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7178-111">備註</span><span class="sxs-lookup"><span data-stu-id="f7178-111">Remarks</span></span>  
 <span data-ttu-id="f7178-112">逸出序列 ({}) 使用，因此可以當做常值字元，在 XAML 中使用左大括弧 （{}）。</span><span class="sxs-lookup"><span data-stu-id="f7178-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="f7178-113">XAML 讀取器通常會使用左大括號 （{}） 來代表標記延伸的進入點; 不過，他們第一次檢查以判斷它是否右大括號 （}） 的下一個字元。</span><span class="sxs-lookup"><span data-stu-id="f7178-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="f7178-114">只有當兩個在大括號 ({}) 都是相鄰，您可以將其認定的逸出序列。</span><span class="sxs-lookup"><span data-stu-id="f7178-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="f7178-115">如果遇到逸出序列時，XAML 讀取器應該處理字串的其餘部分做為字串。</span><span class="sxs-lookup"><span data-stu-id="f7178-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="f7178-116">不過，如果逸出序列套用至具有型別轉換子的成員，字串可能進行類型轉換時將它解譯 XAML 寫入器。</span><span class="sxs-lookup"><span data-stu-id="f7178-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="f7178-117">逸出序列不是標記延伸，而且不受類別。</span><span class="sxs-lookup"><span data-stu-id="f7178-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="f7178-118">不過，它是 （包括自訂 XAML 讀取器） 的 XAML 讀取器應該遵循的慣例。</span><span class="sxs-lookup"><span data-stu-id="f7178-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="f7178-119">引號 （"） 不能以這種方式的逸出序列。</span><span class="sxs-lookup"><span data-stu-id="f7178-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="f7178-120">如果您需要設定為非屬性的屬性值的引號，使用屬性項目語法，將引號字串內的屬性項目，或使用 XML 字元實體。</span><span class="sxs-lookup"><span data-stu-id="f7178-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="f7178-121">內容屬性，引號可以是完整的內容。</span><span class="sxs-lookup"><span data-stu-id="f7178-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="f7178-122">逸出序列 ({}) 指定必須在 XAML 標記延伸位置可能會出現的位置中包含命名空間限定詞的 XML 類型時，就經常需要。</span><span class="sxs-lookup"><span data-stu-id="f7178-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="f7178-123">這包括開頭的 XAML 屬性值，並在標記延伸、 等號 （=） 後面。</span><span class="sxs-lookup"><span data-stu-id="f7178-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="f7178-124">下列範例會顯示在 XAML 屬性值的開頭的 XML 命名空間的逸出序列。</span><span class="sxs-lookup"><span data-stu-id="f7178-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="f7178-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7178-125">See Also</span></span>  
 [<span data-ttu-id="f7178-126">XAML 的類型轉換子和標記延伸</span><span class="sxs-lookup"><span data-stu-id="f7178-126">Type Converters and Markup Extensions for XAML</span></span>](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [<span data-ttu-id="f7178-127">XML 字元實體和 XAML</span><span class="sxs-lookup"><span data-stu-id="f7178-127">XML Character Entities and XAML</span></span>](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
