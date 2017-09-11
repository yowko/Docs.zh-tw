---
title: "get (C# 參考) | Microsoft Docs"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- get_CSharpKeyword
- get
dev_langs:
- CSharp
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 17b64bbbbf4109e47e4765922eec933ea4467e1d
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="get-c-reference"></a><span data-ttu-id="09681-102">get (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="09681-102">get (C# Reference)</span></span>

<span data-ttu-id="09681-103">`get` 關鍵字會在屬性或索引子中定義「存取子」**方法，以傳回屬性值或索引子項目。</span><span class="sxs-lookup"><span data-stu-id="09681-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="09681-104">如需詳細資訊，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)、[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)和[索引子](../../../csharp/programming-guide/indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="09681-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="09681-105">下列範例會為名為 `Seconds` 的屬性定義 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="09681-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="09681-106">它使用名為 `_seconds` 的私用欄位來支援屬性值。</span><span class="sxs-lookup"><span data-stu-id="09681-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 <span data-ttu-id="09681-107">[!code-cs[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="09681-107">[!code-cs[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]</span></span>  
  
<span data-ttu-id="09681-108">`get` 存取子通常是由傳回值的單一陳述式所組成，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="09681-108">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="09681-109">從 C# 7 開始，您可以將 `get` 存取子實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="09681-109">Starting with C# 7, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="09681-110">下列範例會將 `get` 和 `set` 存取子實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="09681-110">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 <span data-ttu-id="09681-111">[!code-cs[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="09681-111">[!code-cs[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]</span></span>   
 
<span data-ttu-id="09681-112">如果屬性的 `get` 和 `set` 存取子只會設定或擷取私用支援欄位中的值，而不會執行其他作業，在此簡單的情況下，您可以利用 C# 編譯器的自動實作屬性支援。</span><span class="sxs-lookup"><span data-stu-id="09681-112">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="09681-113">下列程式碼範例將 `Hours` 實作為自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="09681-113">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 <span data-ttu-id="09681-114">[!code-cs[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="09681-114">[!code-cs[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="09681-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="09681-115">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09681-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09681-116">See Also</span></span>  
 <span data-ttu-id="09681-117">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="09681-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="09681-118"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="09681-118"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="09681-119"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="09681-119"> [C# Keywords](../../../csharp/language-reference/keywords/index.md)
 [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md)</span></span>

