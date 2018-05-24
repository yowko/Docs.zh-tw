---
title: 如何：從 bool? 安全轉型到 bool (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
ms.openlocfilehash: e04e34abd477730f9dd01486ec6bddcde4943edc
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="39c69-102">如何：從 bool? 安全轉型到 bool (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="39c69-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="39c69-103">`bool?` 可為 Null 的型別可以包含三個不同的值︰`true`、`false` 和 `null`。</span><span class="sxs-lookup"><span data-stu-id="39c69-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="39c69-104">因此，`bool?` 類型不能用在有 `if`、`for` 或 `while` 的條件中。</span><span class="sxs-lookup"><span data-stu-id="39c69-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="39c69-105">例如，下列程式碼會導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="39c69-105">For example, the following code causes a compiler error.</span></span>  
  
```csharp  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="39c69-106">這不被允許，因為不清楚 `null` 在條件內容中代表什麼。</span><span class="sxs-lookup"><span data-stu-id="39c69-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="39c69-107">若要在條件陳述式中使用 `bool?`，請先檢查其 <xref:System.Nullable%601.HasValue%2A> 屬性，確定其值不是 `null`，再將它轉換成 `bool`。</span><span class="sxs-lookup"><span data-stu-id="39c69-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="39c69-108">如需詳細資訊，請參閱 [bool](../../../csharp/language-reference/keywords/bool.md)。</span><span class="sxs-lookup"><span data-stu-id="39c69-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="39c69-109">如果您在值為 `null` 的 `bool?` 上執行轉換，則條件測試會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="39c69-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="39c69-110">下例示範從 `bool?` 安全轉型至 `bool` 的一種方法：</span><span class="sxs-lookup"><span data-stu-id="39c69-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="39c69-111">範例</span><span class="sxs-lookup"><span data-stu-id="39c69-111">Example</span></span>  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="39c69-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="39c69-112">See Also</span></span>  
 [<span data-ttu-id="39c69-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="39c69-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="39c69-114">常值關鍵字</span><span class="sxs-lookup"><span data-stu-id="39c69-114">Literal Keywords</span></span>](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [<span data-ttu-id="39c69-115">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="39c69-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="39c69-116">??運算子</span><span class="sxs-lookup"><span data-stu-id="39c69-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
