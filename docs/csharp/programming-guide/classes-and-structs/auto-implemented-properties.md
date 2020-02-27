---
title: 自動實作的屬性 - C# 程式設計手冊
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 989266bfc2de9bd5ce2948f09a2b9f19dd2c782e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628289"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="1486b-102">自動實作的屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1486b-102">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="1486b-103">在 C# 3.0 及更新版本中，當屬性存取子中不需要額外的邏輯時，自動實作的屬性可讓屬性宣告變得更精簡。</span><span class="sxs-lookup"><span data-stu-id="1486b-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="1486b-104">它們還可讓用戶端程式碼建立物件。</span><span class="sxs-lookup"><span data-stu-id="1486b-104">They also enable client code to create objects.</span></span> <span data-ttu-id="1486b-105">當您宣告屬性時，如下列範例所示，編譯器會建立私用、匿名的支援欄位，但只能透過屬性的 `get` 和 `set` 存取子才能存取。</span><span class="sxs-lookup"><span data-stu-id="1486b-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="1486b-106">範例</span><span class="sxs-lookup"><span data-stu-id="1486b-106">Example</span></span>

<span data-ttu-id="1486b-107">下列範例示範一個簡單的類別，其中包含一些自動實作的屬性：</span><span class="sxs-lookup"><span data-stu-id="1486b-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="1486b-108">您無法在介面中宣告自動實作為屬性。</span><span class="sxs-lookup"><span data-stu-id="1486b-108">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="1486b-109">自動執行的屬性會宣告私用實例支援欄位，而介面可能不會宣告實例欄位。</span><span class="sxs-lookup"><span data-stu-id="1486b-109">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="1486b-110">在介面中宣告屬性，而不定義主體，會宣告具有存取子的屬性，而必須由每個實作為介面的型別來執行。</span><span class="sxs-lookup"><span data-stu-id="1486b-110">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="1486b-111">在 C# 6 及更新版本中，您可以初始化自動實作的屬性，就像欄位一樣：</span><span class="sxs-lookup"><span data-stu-id="1486b-111">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
 
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
 
<span data-ttu-id="1486b-112">先前範例中顯示的類別可變動。</span><span class="sxs-lookup"><span data-stu-id="1486b-112">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="1486b-113">用戶端程式代碼可以在建立之後變更物件中的值。</span><span class="sxs-lookup"><span data-stu-id="1486b-113">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="1486b-114">在包含重要行為（方法）和資料的複雜類別中，通常需要有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="1486b-114">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="1486b-115">不過，對於只封裝一組值 (資料) 且只有很少甚至沒有行為的小型類別或結構，您應該將 set 存取子宣告為 [private](../../language-reference/keywords/private.md) (對取用者而言不可變)，或只宣告 get 存取子 (除了建構函式，在其他任何地方都不可變動)，將物件變成不可變動。</span><span class="sxs-lookup"><span data-stu-id="1486b-115">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="1486b-116">如需詳細資訊，請參閱[如何使用自動執行的屬性來執行輕量類別](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1486b-116">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1486b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1486b-117">See also</span></span>

- [<span data-ttu-id="1486b-118">屬性</span><span class="sxs-lookup"><span data-stu-id="1486b-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="1486b-119">修飾詞</span><span class="sxs-lookup"><span data-stu-id="1486b-119">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
