---
title: 參數設計
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 815075198f34c0c045603b9d377b9d5fbdf1a91d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707876"
---
# <a name="parameter-design"></a><span data-ttu-id="eed23-102">參數設計</span><span class="sxs-lookup"><span data-stu-id="eed23-102">Parameter Design</span></span>

<span data-ttu-id="eed23-103">本節提供有關參數設計的廣泛指導方針，包括具有檢查引數之指導方針的章節。</span><span class="sxs-lookup"><span data-stu-id="eed23-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="eed23-104">此外，您應該參考 [具名引數](naming-parameters.md)中所述的指導方針。</span><span class="sxs-lookup"><span data-stu-id="eed23-104">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="eed23-105">✔️會使用提供成員所需功能的最不衍生參數類型。</span><span class="sxs-lookup"><span data-stu-id="eed23-105">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="eed23-106">例如，假設您想要設計一個列舉集合的方法，並將每個專案列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="eed23-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="eed23-107">例如，這種方法應該採用做 <xref:System.Collections.IEnumerable> 為參數，而不是 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.IList> 。</span><span class="sxs-lookup"><span data-stu-id="eed23-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="eed23-108">❌ 請勿使用保留的參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-108">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="eed23-109">如果在未來的版本中需要更多的成員輸入，可以加入新的多載。</span><span class="sxs-lookup"><span data-stu-id="eed23-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="eed23-110">❌ 沒有公開公開的方法，這些方法會採用指標、指標陣列或多維陣列作為參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-110">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="eed23-111">指標和多維陣列相當難以正確使用。</span><span class="sxs-lookup"><span data-stu-id="eed23-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="eed23-112">在幾乎所有情況下，Api 都可以重新設計，以避免將這些類型視為參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="eed23-113">✔️請將所有參數都放在所有的傳 `out` 值和 `ref` 參數之後 (排除參數陣列) ，即使這會導致多載之間的參數順序不一致 (看到 [成員](member-overloading.md) 多載) 。</span><span class="sxs-lookup"><span data-stu-id="eed23-113">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="eed23-114">這些 `out` 參數可以視為額外的傳回值，並將它們群組在一起，讓方法簽章更容易理解。</span><span class="sxs-lookup"><span data-stu-id="eed23-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="eed23-115">覆寫成員或實介面成員時，✔️在具名引數中是一致的。</span><span class="sxs-lookup"><span data-stu-id="eed23-115">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="eed23-116">這會更妥善地傳達方法之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="eed23-116">This better communicates the relationship between the methods.</span></span>

### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="eed23-117">選擇列舉和布林值參數</span><span class="sxs-lookup"><span data-stu-id="eed23-117">Choosing Between Enum and Boolean Parameters</span></span>  

 <span data-ttu-id="eed23-118">如果成員另有兩個或多個布林值參數，✔️請使用列舉。</span><span class="sxs-lookup"><span data-stu-id="eed23-118">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="eed23-119">❌ 除非您絕對確定永遠不需要兩個以上的值，否則請勿使用布林值。</span><span class="sxs-lookup"><span data-stu-id="eed23-119">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="eed23-120">列舉可讓您有一些空間可讓您在未來加入值，但您應該留意到 [列舉設計](enum.md)中所述，將值新增至列舉的所有含意。</span><span class="sxs-lookup"><span data-stu-id="eed23-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="eed23-121">✔️考慮將布林值用於真正是雙狀態值的函式參數，而且只是用來初始化布林值屬性。</span><span class="sxs-lookup"><span data-stu-id="eed23-121">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validating-arguments"></a><span data-ttu-id="eed23-122">驗證引數</span><span class="sxs-lookup"><span data-stu-id="eed23-122">Validating Arguments</span></span>

 <span data-ttu-id="eed23-123">✔️確實會驗證傳遞給公用、受保護或明確執行之成員的引數。</span><span class="sxs-lookup"><span data-stu-id="eed23-123">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="eed23-124"><xref:System.ArgumentException?displayProperty=nameWithType>如果驗證失敗，則擲回或其中一個子類別。</span><span class="sxs-lookup"><span data-stu-id="eed23-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="eed23-125">請注意，實際的驗證不一定要在公用或受保護成員本身發生。</span><span class="sxs-lookup"><span data-stu-id="eed23-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="eed23-126">它可能會在某個私用或內部常式的較低層級發生。</span><span class="sxs-lookup"><span data-stu-id="eed23-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="eed23-127">主要點是公開給終端使用者的整個介面區會檢查引數。</span><span class="sxs-lookup"><span data-stu-id="eed23-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="eed23-128"><xref:System.ArgumentNullException>如果傳遞了 null 引數，而且該成員不支援 null 引數，✔️會擲回。</span><span class="sxs-lookup"><span data-stu-id="eed23-128">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="eed23-129">✔️驗證列舉參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-129">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="eed23-130">請勿假設列舉引數會在列舉所定義的範圍內。</span><span class="sxs-lookup"><span data-stu-id="eed23-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="eed23-131">CLR 允許將任何整數值轉換為列舉值，即使值未在列舉中定義。</span><span class="sxs-lookup"><span data-stu-id="eed23-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="eed23-132">❌ 請勿用於 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 列舉範圍檢查。</span><span class="sxs-lookup"><span data-stu-id="eed23-132">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="eed23-133">✔️請注意，可變動的引數在驗證之後可能已變更。</span><span class="sxs-lookup"><span data-stu-id="eed23-133">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="eed23-134">如果成員具有安全性敏感性，建議您建立複本，然後驗證並處理引數。</span><span class="sxs-lookup"><span data-stu-id="eed23-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="parameter-passing"></a><span data-ttu-id="eed23-135">參數傳遞</span><span class="sxs-lookup"><span data-stu-id="eed23-135">Parameter Passing</span></span>

 <span data-ttu-id="eed23-136">從架構設計工具的觀點來看，有三個主要的參數群組：傳值參數、 `ref` 參數和 `out` 參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="eed23-137">當引數透過傳值參數傳遞時，該成員會收到傳入的實際引數複本。</span><span class="sxs-lookup"><span data-stu-id="eed23-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="eed23-138">如果引數是實值型別，則會將引數的複本放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="eed23-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="eed23-139">如果引數是參考型別，則會在堆疊上放置參考的複本。</span><span class="sxs-lookup"><span data-stu-id="eed23-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="eed23-140">最熱門 CLR 語言（例如 c #、VB.NET 和 c + +）預設為以傳值方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="eed23-141">當引數透過參數傳遞時 `ref` ，該成員會收到傳入的實際引數參考。</span><span class="sxs-lookup"><span data-stu-id="eed23-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="eed23-142">如果引數是實值型別，則會將引數的參考放置在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="eed23-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="eed23-143">如果引數是參考型別，則參考的參考會放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="eed23-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="eed23-144">`Ref` 參數可以用來允許成員修改呼叫端所傳遞的引數。</span><span class="sxs-lookup"><span data-stu-id="eed23-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="eed23-145">`Out` 參數類似于 `ref` 參數，但有一些小差異。</span><span class="sxs-lookup"><span data-stu-id="eed23-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="eed23-146">此參數一開始視為未指派，且在指派一些值之前無法在成員主體中讀取。</span><span class="sxs-lookup"><span data-stu-id="eed23-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="eed23-147">此外，必須在成員傳回之前，將某個值指派給參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-147">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="eed23-148">❌ 請避免使用 `out` 或 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-148">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="eed23-149">使用 `out` 或 `ref` 參數需要使用指標的經驗、瞭解實值型別和參考型別有何不同，以及處理具有多個傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="eed23-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="eed23-150">此外，和參數之間的差異 `out` 並 `ref` 不大易懂。</span><span class="sxs-lookup"><span data-stu-id="eed23-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="eed23-151">設計一般物件的架構架構設計人員不應預期使用者使用 `out` 或 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="eed23-152">❌ 請勿以傳址方式傳遞參考型別。</span><span class="sxs-lookup"><span data-stu-id="eed23-152">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="eed23-153">規則有一些有限的例外狀況，例如可用來交換參考的方法。</span><span class="sxs-lookup"><span data-stu-id="eed23-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="eed23-154">具有可變參數數目的成員</span><span class="sxs-lookup"><span data-stu-id="eed23-154">Members with Variable Number of Parameters</span></span>

 <span data-ttu-id="eed23-155">可採用可變數目引數的成員會藉由提供陣列參數來表示。</span><span class="sxs-lookup"><span data-stu-id="eed23-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="eed23-156">例如， <xref:System.String> 提供下列方法：</span><span class="sxs-lookup"><span data-stu-id="eed23-156">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="eed23-157">然後，使用者可以呼叫方法，如下所示 <xref:System.String.Format%2A?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="eed23-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="eed23-158">將 c # params 關鍵字加入至陣列參數，會將參數變更為所謂的 params 陣列參數，並提供建立暫存陣列的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="eed23-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="eed23-159">這麼做可讓使用者藉由直接在引數清單中傳遞陣列元素來呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="eed23-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="eed23-160">請注意，您只能將 params 關鍵字加入至參數清單中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="eed23-161">如果您希望終端使用者傳遞具有少量專案的陣列，✔️可考慮將 params 關鍵字加入至陣列參數。</span><span class="sxs-lookup"><span data-stu-id="eed23-161">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="eed23-162">如果預期會在常見的案例中傳遞大量元素，則使用者可能不會以內嵌方式傳遞這些元素，因此不需要 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="eed23-162">If it's expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="eed23-163">❌ 如果呼叫端幾乎一律具有已在陣列中的輸入，請避免使用 params 陣列。</span><span class="sxs-lookup"><span data-stu-id="eed23-163">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="eed23-164">例如，具有位元組陣列參數的成員幾乎不會藉由傳遞個別位元組來呼叫。</span><span class="sxs-lookup"><span data-stu-id="eed23-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="eed23-165">基於這個理由，.NET Framework 中的位元組陣列參數不使用 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="eed23-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="eed23-166">❌ 如果接受 params 陣列參數的成員修改陣列，請不要使用 params 陣列。</span><span class="sxs-lookup"><span data-stu-id="eed23-166">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="eed23-167">因為許多編譯器會將成員的引數轉換成呼叫位置上的暫存陣列，所以陣列可能是暫時的物件，因此對陣列所做的任何修改都將遺失。</span><span class="sxs-lookup"><span data-stu-id="eed23-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="eed23-168">✔️請考慮在簡單多載中使用 params 關鍵字，即使更複雜的多載無法使用它也是一樣。</span><span class="sxs-lookup"><span data-stu-id="eed23-168">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="eed23-169">如果使用者在一個多載中有參數陣列的值，即使它不在所有多載中，也會詢問您。</span><span class="sxs-lookup"><span data-stu-id="eed23-169">Ask yourself if users would value having the params array in one overload even if it wasn't in all overloads.</span></span>

 <span data-ttu-id="eed23-170">✔️請嘗試排序參數，讓它可以使用 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="eed23-170">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="eed23-171">✔️考慮提供特殊的多載和程式碼路徑，以便在極具效能效益的 Api 中使用少量引數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="eed23-171">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="eed23-172">這可以避免在使用少量引數呼叫 API 時建立陣列物件。</span><span class="sxs-lookup"><span data-stu-id="eed23-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="eed23-173">藉由採用單一形式的陣列參數並加入數值尾碼，形成參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="eed23-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="eed23-174">只有當您要在整個程式碼路徑中使用特殊案例，而不只是建立陣列並呼叫更一般的方法時，才應該這樣做。</span><span class="sxs-lookup"><span data-stu-id="eed23-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="eed23-175">✔️請注意，null 可以做為 params 陣列引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="eed23-175">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="eed23-176">在處理之前，您應該先驗證陣列是否為非 null。</span><span class="sxs-lookup"><span data-stu-id="eed23-176">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="eed23-177">❌ 請勿使用 `varargs` 方法，也稱為省略號。</span><span class="sxs-lookup"><span data-stu-id="eed23-177">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="eed23-178">某些 CLR 語言（例如 c + +）支援傳遞變數參數清單（稱為方法）的替代慣例 `varargs` 。</span><span class="sxs-lookup"><span data-stu-id="eed23-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="eed23-179">慣例不應用於架構，因為它不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="eed23-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="eed23-180">指標參數</span><span class="sxs-lookup"><span data-stu-id="eed23-180">Pointer Parameters</span></span>

 <span data-ttu-id="eed23-181">一般而言，指標不應該出現在設計完善之 managed 程式碼架構的公用介面區中。</span><span class="sxs-lookup"><span data-stu-id="eed23-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="eed23-182">大部分的情況下，都應該封裝指標。</span><span class="sxs-lookup"><span data-stu-id="eed23-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="eed23-183">不過，在某些情況下，基於互通性原因需要指標，而在這種情況下使用指標是適當的。</span><span class="sxs-lookup"><span data-stu-id="eed23-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="eed23-184">因為指標不符合 CLS 規範，所以✔️確實提供任何採用指標引數之成員的替代方法。</span><span class="sxs-lookup"><span data-stu-id="eed23-184">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="eed23-185">❌ 避免對指標引數進行昂貴的引數檢查。</span><span class="sxs-lookup"><span data-stu-id="eed23-185">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="eed23-186">當您設計具有指標的成員時，✔️會遵循一般指標相關慣例。</span><span class="sxs-lookup"><span data-stu-id="eed23-186">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="eed23-187">例如，不需要傳遞開始索引，因為可以使用簡單的指標算術來完成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="eed23-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="eed23-188">*部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="eed23-188">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="eed23-189">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="eed23-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="eed23-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eed23-190">See also</span></span>

- [<span data-ttu-id="eed23-191">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="eed23-191">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="eed23-192">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="eed23-192">Framework Design Guidelines</span></span>](index.md)
