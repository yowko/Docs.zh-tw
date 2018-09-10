---
title: 自動實作的屬性 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 0d32dfd626cb8484e935dd0e8608c2e29d3ecbde
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44228074"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="b3707-102">自動實作的屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b3707-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="b3707-103">在 C# 3.0 及更新版本中，當屬性存取子中不需要額外的邏輯時，自動實作的屬性可讓屬性宣告變得更精簡。</span><span class="sxs-lookup"><span data-stu-id="b3707-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="b3707-104">它們還可讓用戶端程式碼建立物件。</span><span class="sxs-lookup"><span data-stu-id="b3707-104">They also enable client code to create objects.</span></span> <span data-ttu-id="b3707-105">當您宣告屬性時，如下列範例所示，編譯器會建立私用、匿名的支援欄位，但只能透過屬性的 `get` 和 `set` 存取子才能存取。</span><span class="sxs-lookup"><span data-stu-id="b3707-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3707-106">範例</span><span class="sxs-lookup"><span data-stu-id="b3707-106">Example</span></span>  
 <span data-ttu-id="b3707-107">下列範例示範一個簡單的類別，其中包含一些自動實作的屬性：</span><span class="sxs-lookup"><span data-stu-id="b3707-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="b3707-108">在 C# 6 及更新版本中，您可以初始化自動實作的屬性，就像欄位一樣：</span><span class="sxs-lookup"><span data-stu-id="b3707-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="b3707-109">先前範例中顯示的類別可變動。</span><span class="sxs-lookup"><span data-stu-id="b3707-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="b3707-110">用戶端程式碼可以在物件建立之後變更其中的值。</span><span class="sxs-lookup"><span data-stu-id="b3707-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="b3707-111">在包含重要行為 (方法) 和資料的複雜類別中，通常需要有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="b3707-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="b3707-112">不過，對於只封裝一組值 (資料) 且只有很少甚至沒有行為的小型類別或結構，您應該將 set 存取子宣告為 [private](../../../csharp/language-reference/keywords/private.md) (對取用者而言不可變)，或只宣告 get 存取子 (除了建構函式，在其他任何地方都不可變動)，將物件變成不可變動。</span><span class="sxs-lookup"><span data-stu-id="b3707-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="b3707-113">如需詳細資訊，請參閱[如何：使用自動實作的屬性來實作輕量型類別](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b3707-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="b3707-114">自動實作的屬性 (Property) 上允許有屬性 (Attribute)，但在支援欄位上顯然不允許，因為從原始程式碼無法存取這些欄位。</span><span class="sxs-lookup"><span data-stu-id="b3707-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="b3707-115">如果您必須在屬性 (Property) 的支援欄位上使用屬性 (Attribute)，請建立一般屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="b3707-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3707-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3707-116">See Also</span></span>

- [<span data-ttu-id="b3707-117">屬性</span><span class="sxs-lookup"><span data-stu-id="b3707-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="b3707-118">修飾詞</span><span class="sxs-lookup"><span data-stu-id="b3707-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
