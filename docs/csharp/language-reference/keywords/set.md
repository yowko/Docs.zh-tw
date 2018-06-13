---
title: set (C# 參考)
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 5baab41a0f9fc81bbf9f606ef569f0653b873e26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265784"
---
# <a name="set-c-reference"></a><span data-ttu-id="96df2-102">set (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="96df2-102">set (C# Reference)</span></span>
<span data-ttu-id="96df2-103">`set` 關鍵字會在屬性或索引子中定義「存取子」方法，以將值指派給屬性或索引子項目。</span><span class="sxs-lookup"><span data-stu-id="96df2-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="96df2-104">如需詳細資訊和範例，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)、[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)和[索引子](../../../csharp/programming-guide/indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="96df2-104">For more information and examples, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="96df2-105">下列範例會為名為 `Seconds` 的屬性定義 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="96df2-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="96df2-106">它使用名為 `_seconds` 的私用欄位來支援屬性值。</span><span class="sxs-lookup"><span data-stu-id="96df2-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

<span data-ttu-id="96df2-107">`set` 存取子通常是由傳回值的單一陳述式所組成，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="96df2-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="96df2-108">從 C# 7.0 開始，您可以將 `set` 存取子實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="96df2-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="96df2-109">下列範例會將 `get` 和 `set` 存取子實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="96df2-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
<span data-ttu-id="96df2-110">如果屬性的 `get` 和 `set` 存取子只會設定或擷取私用支援欄位中的值，而不會執行其他作業，則在此簡單的情況下，您可以利用 C# 編譯器的自動實作屬性支援。</span><span class="sxs-lookup"><span data-stu-id="96df2-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="96df2-111">下列程式碼範例會將 `Hours` 實作為自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="96df2-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a><span data-ttu-id="96df2-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="96df2-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="96df2-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="96df2-113">See Also</span></span>  
 [<span data-ttu-id="96df2-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="96df2-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="96df2-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="96df2-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="96df2-116">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="96df2-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="96df2-117">屬性</span><span class="sxs-lookup"><span data-stu-id="96df2-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
