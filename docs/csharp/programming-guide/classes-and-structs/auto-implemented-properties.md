---
title: "自動實作的屬性 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: 23
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 92e0037b73f1054673ea8060b71af5bd4db13ca3
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="8d8a6-102">自動實作的屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="8d8a6-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="8d8a6-103">在 C# 3.0 及更新版本中，當屬性存取子中不需要額外的邏輯時，自動實作的屬性可讓屬性宣告變得更精簡。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="8d8a6-104">它們還可讓用戶端程式碼建立物件。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-104">They also enable client code to create objects.</span></span> <span data-ttu-id="8d8a6-105">當您宣告屬性時，如下列範例所示，編譯器會建立私用、匿名的支援欄位，但只能透過屬性的 `get` 和 `set` 存取子才能存取。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d8a6-106">範例</span><span class="sxs-lookup"><span data-stu-id="8d8a6-106">Example</span></span>  
 <span data-ttu-id="8d8a6-107">下列範例示範一個簡單的類別，其中包含一些自動實作的屬性：</span><span class="sxs-lookup"><span data-stu-id="8d8a6-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 <span data-ttu-id="8d8a6-108">[!code-cs[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8d8a6-108">[!code-cs[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]</span></span>  
  
 <span data-ttu-id="8d8a6-109">在 C# 6 及更新版本中，您可以初始化自動實作的屬性，就像欄位一樣：</span><span class="sxs-lookup"><span data-stu-id="8d8a6-109">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="8d8a6-110">先前範例中顯示的類別可變動。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-110">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="8d8a6-111">用戶端程式碼可以在物件建立之後變更其中的值。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-111">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="8d8a6-112">在包含重要行為 (方法) 和資料的複雜類別中，通常需要有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-112">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="8d8a6-113">不過，對於只封裝一組值 (資料) 且只有很少甚至沒有行為的小型類別或結構，您應該將 set 存取子宣告為 [private](../../../csharp/language-reference/keywords/private.md) (對取用者而言不可變)，或只宣告 get 存取子 (除了建構函式，在其他任何地方都不可變動)，將物件變成不可變動。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-113">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="8d8a6-114">如需詳細資訊，請參閱[如何：使用自動實作的屬性來實作輕量型類別](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-114">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="8d8a6-115">自動實作的屬性 (Property) 上允許有屬性 (Attribute)，但在支援欄位上顯然不允許，因為從原始程式碼無法存取這些欄位。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-115">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="8d8a6-116">如果您必須在屬性 (Property) 的支援欄位上使用屬性 (Attribute)，請建立一般屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="8d8a6-116">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8a6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d8a6-117">See Also</span></span>  
 <span data-ttu-id="8d8a6-118">[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="8d8a6-118">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 [<span data-ttu-id="8d8a6-119">修飾詞</span><span class="sxs-lookup"><span data-stu-id="8d8a6-119">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

