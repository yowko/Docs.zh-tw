---
title: 使用索引子 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 3e4c1f346b83cf97c57a359984bd08e075b6451b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253217"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="d8922-102">使用索引子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d8922-102">Using Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="d8922-103">索引子是語法便利性，可讓您建立用戶端應用程式可以就像陣列一樣地存取的 [class](../../../csharp/language-reference/keywords/class.md)、[struct](../../../csharp/language-reference/keywords/struct.md) 或 [interface](../../../csharp/language-reference/keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="d8922-103">Indexers are a syntactic convenience that enable you to create a [class](../../../csharp/language-reference/keywords/class.md), [struct](../../../csharp/language-reference/keywords/struct.md), or [interface](../../../csharp/language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="d8922-104">索引子最常實作於類型中，而類型的主要用途是封裝內部集合或陣列。</span><span class="sxs-lookup"><span data-stu-id="d8922-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="d8922-105">例如，假設您的 TempRecord 類別將華氏溫度代表為 24 小時期間記錄於 10 個不同的時間。</span><span class="sxs-lookup"><span data-stu-id="d8922-105">For example, suppose you have a class named TempRecord that represents the temperature in Farenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="d8922-106">這個類別包含浮點類型的 "temps" 陣列以代表溫度，以及代表溫度記錄日期的 <xref:System.DateTime>。</span><span class="sxs-lookup"><span data-stu-id="d8922-106">The class contains an array named "temps" of type float to represent the temperatures, and a <xref:System.DateTime> that represents the date the temperatures were recorded.</span></span> <span data-ttu-id="d8922-107">在此類別中實作索引子，用戶端即可將 TempRecord 執行個體中的溫度存取為 `float temp = tr[4]`，而不是 `float temp = tr.temps[4]`。</span><span class="sxs-lookup"><span data-stu-id="d8922-107">By implementing an indexer in this class, clients can access the temperatures in a TempRecord instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="d8922-108">索引子標記法不僅可簡化用戶端應用程式的語法，還可以讓其他開發人員更直覺地了解類別其用途。</span><span class="sxs-lookup"><span data-stu-id="d8922-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
 <span data-ttu-id="d8922-109">若要在類別或結構上宣告索引子，請使用 [this](../../../csharp/language-reference/keywords/this.md) 關鍵字，如此範例所示：</span><span class="sxs-lookup"><span data-stu-id="d8922-109">To declare an indexer on a class or struct, use the [this](../../../csharp/language-reference/keywords/this.md) keyword, as in this example:</span></span>  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="d8922-110">備註</span><span class="sxs-lookup"><span data-stu-id="d8922-110">Remarks</span></span>  
 <span data-ttu-id="d8922-111">索引子類型和其參數類型至少必須可以像索引子本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="d8922-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="d8922-112">如需存取範圍層級的詳細資訊，請參閱[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="d8922-112">For more information about accessibility levels, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="d8922-113">如需如何搭配使用索引子與介面的詳細資訊，請參閱[介面索引子](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="d8922-113">For more information about how to use indexers with an interface, see [Interface Indexers](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="d8922-114">索引子的簽章包含其型式參數的數目和類型。</span><span class="sxs-lookup"><span data-stu-id="d8922-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="d8922-115">它不包含索引子類型或型式參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8922-115">It does not include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="d8922-116">如果您在相同的類別中宣告多個索引子，則它們必須具有不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="d8922-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="d8922-117">索引子值不會分類為變數；因此，您無法將索引子值傳遞為 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="d8922-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="d8922-118">若要提供具有其他語言可使用之名稱的索引子，請在宣告中使用 `name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d8922-118">To provide the indexer with a name that other languages can use, use a `name` attribute in the declaration.</span></span> <span data-ttu-id="d8922-119">例如: </span><span class="sxs-lookup"><span data-stu-id="d8922-119">For example:</span></span>  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 <span data-ttu-id="d8922-120">這個索引子的名稱會是 `TheItem`。</span><span class="sxs-lookup"><span data-stu-id="d8922-120">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="d8922-121">未提供名稱屬性會將 `Item` 設為預設名稱。</span><span class="sxs-lookup"><span data-stu-id="d8922-121">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="d8922-122">範例 1</span><span class="sxs-lookup"><span data-stu-id="d8922-122">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="d8922-123">描述</span><span class="sxs-lookup"><span data-stu-id="d8922-123">Description</span></span>  
 <span data-ttu-id="d8922-124">下列範例示範如何宣告私用陣列欄位 `temps` 和索引子。</span><span class="sxs-lookup"><span data-stu-id="d8922-124">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="d8922-125">索引子可讓您直接存取執行個體 `tempRecord[i]`。</span><span class="sxs-lookup"><span data-stu-id="d8922-125">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="d8922-126">使用索引子的替代方式是將陣列宣告為 [public](../../../csharp/language-reference/keywords/public.md) 成員，並直接存取其成員 `tempRecord.temps[i]`。</span><span class="sxs-lookup"><span data-stu-id="d8922-126">The alternative to using the indexer is to declare the array as a [public](../../../csharp/language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="d8922-127">請注意，評估索引子的存取時 (例如，在 `Console.Write` 陳述式中)，會叫用 [get](../../../csharp/language-reference/keywords/get.md) 存取子。</span><span class="sxs-lookup"><span data-stu-id="d8922-127">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../../csharp/language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="d8922-128">因此，如果沒有 `get` 存取子，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8922-128">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d8922-129">程式碼</span><span class="sxs-lookup"><span data-stu-id="d8922-129">Code</span></span>  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="d8922-130">使用其他值編製索引</span><span class="sxs-lookup"><span data-stu-id="d8922-130">Indexing Using Other Values</span></span>  
 <span data-ttu-id="d8922-131">C# 不會將索引類型限制為整數。</span><span class="sxs-lookup"><span data-stu-id="d8922-131">C# does not limit the index type to integer.</span></span> <span data-ttu-id="d8922-132">例如，搭配使用字串與索引子可能十分有用。</span><span class="sxs-lookup"><span data-stu-id="d8922-132">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="d8922-133">在集合中搜尋字串，並傳回適當的值，可能會實作這類索引子。</span><span class="sxs-lookup"><span data-stu-id="d8922-133">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="d8922-134">多載存取子時，字串和整數版本可以共存。</span><span class="sxs-lookup"><span data-stu-id="d8922-134">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="d8922-135">範例 2</span><span class="sxs-lookup"><span data-stu-id="d8922-135">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="d8922-136">描述</span><span class="sxs-lookup"><span data-stu-id="d8922-136">Description</span></span>  
 <span data-ttu-id="d8922-137">在此範例中，宣告的類別會儲存週中的日。</span><span class="sxs-lookup"><span data-stu-id="d8922-137">In this example, a class is declared that stores the days of the week.</span></span> <span data-ttu-id="d8922-138">宣告接受日名稱字串的 `get` 存取子，並傳回對應整數。</span><span class="sxs-lookup"><span data-stu-id="d8922-138">A `get` accessor is declared that takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="d8922-139">例如，星期日會傳回 0、星期一會傳回 1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="d8922-139">For example, Sunday will return 0, Monday will return 1, and so on.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d8922-140">程式碼</span><span class="sxs-lookup"><span data-stu-id="d8922-140">Code</span></span>  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d8922-141">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d8922-141">Robust Programming</span></span>  
 <span data-ttu-id="d8922-142">有兩種主要的方式可以改善索引子的安全性和可靠性：</span><span class="sxs-lookup"><span data-stu-id="d8922-142">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
-   <span data-ttu-id="d8922-143">請務必包含某種類型的錯誤處理策略來處理用戶端程式碼傳入無效索引值的機會。</span><span class="sxs-lookup"><span data-stu-id="d8922-143">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="d8922-144">在本主題稍早的第一個範例中，TempRecord 類別提供 Length 屬性，以讓用戶端程式碼先確認輸入，再將其傳遞給索引子。</span><span class="sxs-lookup"><span data-stu-id="d8922-144">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="d8922-145">您也可以將錯誤處理程式碼放在索引子本身內。</span><span class="sxs-lookup"><span data-stu-id="d8922-145">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="d8922-146">請務必為使用者記載您在索引子存取子內擲回的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d8922-146">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
-   <span data-ttu-id="d8922-147">將 `get` 和 [set](../../../csharp/language-reference/keywords/set.md) 存取子的存取範圍設定為合理限制。</span><span class="sxs-lookup"><span data-stu-id="d8922-147">Set the accessibility of the `get` and [set](../../../csharp/language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="d8922-148">這對 `set` 存取子特別重要。</span><span class="sxs-lookup"><span data-stu-id="d8922-148">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="d8922-149">如需詳細資訊，請參閱[限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)。</span><span class="sxs-lookup"><span data-stu-id="d8922-149">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8922-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8922-150">See Also</span></span>

- [<span data-ttu-id="d8922-151">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d8922-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d8922-152">索引子</span><span class="sxs-lookup"><span data-stu-id="d8922-152">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="d8922-153">屬性</span><span class="sxs-lookup"><span data-stu-id="d8922-153">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
