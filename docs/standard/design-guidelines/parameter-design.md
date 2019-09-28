---
title: 參數設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: KrzysztofCwalina
ms.openlocfilehash: 28b00f5911bb47536ec44b96f284e47b6c671149
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353738"
---
# <a name="parameter-design"></a><span data-ttu-id="bcbb2-102">參數設計</span><span class="sxs-lookup"><span data-stu-id="bcbb2-102">Parameter Design</span></span>
<span data-ttu-id="bcbb2-103">本節提供有關參數設計的廣泛指導方針，包括包含檢查引數之指導方針的章節。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="bcbb2-104">此外，您應該參考[具名引數](../../../docs/standard/design-guidelines/naming-parameters.md)中所述的指導方針。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="bcbb2-105">**✓ DO** 使用至少衍生的參數類型，提供成員所需的功能。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="bcbb2-106">例如，假設您想要設計一個列舉集合的方法，並將每個專案列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="bcbb2-107">例如，這類方法應該以 <xref:System.Collections.IEnumerable> 做為參數，而不是 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.IList>。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="bcbb2-108">**X DO NOT** 使用保留的參數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="bcbb2-109">如果某些未來版本中需要更多的成員輸入，則可以加入新的多載。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="bcbb2-110">**X DO NOT** 有公開這些方法會採用指標、 陣列的指標或做為參數的多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="bcbb2-111">指標和多維陣列相對較難正確使用。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="bcbb2-112">幾乎在所有情況下，都可以重新設計 Api，以避免將這些類型當做參數來採用。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="bcbb2-113">**✓ DO** 放置所有 `out` 遵循所有由值參數和 `ref` 參數 （不含參數陣列），即使它會造成不一致的參數多載之間的順序 (請參閱 [成員多載 ](../../../docs/standard/design-guidelines/member-overloading.md))。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="bcbb2-114">@No__t-0 參數可以視為額外的傳回值，並將它們分組在一起，讓方法簽章更容易瞭解。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="bcbb2-115">**✓ DO** 一致時覆寫成員命名的參數，或實作介面成員中。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="bcbb2-116">這會更有效地傳達方法之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="bcbb2-117">選擇列舉和布林值參數</span><span class="sxs-lookup"><span data-stu-id="bcbb2-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="bcbb2-118">**✓ DO** 如果成員原本必須另外兩個或多個布林值參數使用的列舉。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="bcbb2-119">**X DO NOT** 使用布林值，除非您完全確定永遠不會需要兩個以上的值。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="bcbb2-120">列舉可讓您在未來新增值時提供一些空間，但您應該瞭解將值加入至列舉的所有含意，這些都是在[Enum 設計](../../../docs/standard/design-guidelines/enum.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="bcbb2-121">**✓ CONSIDER** 使用建構函式參數是真正的兩個狀態的值，只會用來初始化布林值屬性的布林值。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="bcbb2-122">驗證引數</span><span class="sxs-lookup"><span data-stu-id="bcbb2-122">Validating Arguments</span></span>  
 <span data-ttu-id="bcbb2-123">**✓ DO** 驗證引數傳遞至 public、 protected 或明確實作的成員。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="bcbb2-124">如果驗證失敗，則擲回 <xref:System.ArgumentException?displayProperty=nameWithType> 或它的其中一個子類別。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="bcbb2-125">請注意，實際的驗證不一定要在公用或受保護的成員本身發生。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="bcbb2-126">在某些私用或內部常式的較低層級，可能會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="bcbb2-127">主要的重點是，向使用者公開的整個介面區都會檢查引數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="bcbb2-128">**✓ DO** 擲回 <xref:System.ArgumentNullException> 如果傳遞 null 引數，而且成員不支援 null 引數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="bcbb2-129">**✓ DO** 驗證列舉的參數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="bcbb2-130">「不要」假設列舉引數會在列舉所定義的範圍內。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="bcbb2-131">CLR 允許將任何整數值轉換為列舉值，即使列舉中未定義此值。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="bcbb2-132">**X DO NOT** 使用 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 列舉範圍檢查。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="bcbb2-133">**✓ DO** 注意之後他們已驗證，可能已經變更可變動的引數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="bcbb2-134">如果成員區分安全性，建議您建立複本，然後驗證和處理引數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="bcbb2-135">參數傳遞</span><span class="sxs-lookup"><span data-stu-id="bcbb2-135">Parameter Passing</span></span>  
 <span data-ttu-id="bcbb2-136">從架構設計工具的觀點來看，有三個主要的參數群組：傳值參數、@no__t 0 參數和 @no__t 1 參數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="bcbb2-137">透過傳值參數傳遞引數時，成員會收到傳入的實際引數複本。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="bcbb2-138">如果引數是實值型別，則引數的複本會放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="bcbb2-139">如果引數是參考型別，則會將參考的複本放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="bcbb2-140">最受歡迎的 CLR 語言， C#例如、VB.NET 和C++，預設為以傳值方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="bcbb2-141">透過 `ref` 參數傳遞引數時，成員會收到傳入之實際引數的參考。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="bcbb2-142">如果引數是實值型別，則引數的參考會放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="bcbb2-143">如果引數是參考型別，參考的參考會放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="bcbb2-144">`Ref` 參數可以用來允許成員修改呼叫者所傳遞的引數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="bcbb2-145">`Out` 參數類似于 `ref` 參數，但有一些小差異。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="bcbb2-146">參數最初被視為未指派，而且在指派某個值之前，無法在成員主體中讀取。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="bcbb2-147">此外，必須在成員傳回之前，先指派一些值給參數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="bcbb2-148">**X AVOID** 使用 `out` 或 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="bcbb2-149">使用 `out` 或 @no__t 1 參數需要使用指標的經驗、瞭解實數值型別和參考型別之間的差異，以及處理具有多個傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="bcbb2-150">此外，和`ref`參數之間`out`的差異也無法廣泛瞭解。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="bcbb2-151">一般物件的架構架構設計人員應該不會預期使用者會使用 `out` 或 @no__t 1 參數來主控。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="bcbb2-152">**X DO NOT** 傳址方式傳遞參考型別。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="bcbb2-153">規則有一些有限的例外狀況，例如可以用來交換參考的方法。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="bcbb2-154">具有可變參數數目的成員</span><span class="sxs-lookup"><span data-stu-id="bcbb2-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="bcbb2-155">可以接受可變數目引數的成員會藉由提供陣列參數來表示。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="bcbb2-156">例如，<xref:System.String> 提供下列方法：</span><span class="sxs-lookup"><span data-stu-id="bcbb2-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```csharp  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="bcbb2-157">然後，使用者可以呼叫 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bcbb2-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="bcbb2-158">將C# params 關鍵字新增至陣列參數會將參數變更為所謂的 params 陣列參數，並提供建立暫存陣列的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```csharp  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="bcbb2-159">這麼做可讓使用者直接在引數清單中傳遞陣列元素，藉以呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="bcbb2-160">請注意，params 關鍵字只能加入至參數清單中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="bcbb2-161">**✓ CONSIDER** params 關鍵字加入陣列參數，如果您預期使用者會傳遞具有少數的元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="bcbb2-162">如果預期會在常見的案例中傳遞許多元素，則使用者可能不會以內嵌方式傳遞這些專案，因此不需要 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="bcbb2-163">**X AVOID** 使用參數陣列，如果呼叫端會幾乎都已經輸入陣列中。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="bcbb2-164">例如，具有位元組陣列參數的成員幾乎不會藉由傳遞個別位元組來呼叫。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="bcbb2-165">因此，.NET Framework 中的位元組陣列參數不會使用 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="bcbb2-166">**X DO NOT** 使用參數陣列，如果陣列修改採取 params 陣列參數的成員。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="bcbb2-167">因為許多編譯器會將成員的引數轉換成呼叫位置的臨時陣列，所以陣列可能是暫存物件，因此對陣列所做的任何修改都將遺失。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="bcbb2-168">**✓ CONSIDER** 使用 params 關鍵字，在簡單的多載中，即使有更複雜的多載無法使用。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="bcbb2-169">詢問您是否要讓使用者在一個多載中具有 params 陣列值，即使它不在所有多載中也一樣。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="bcbb2-170">**✓ DO** 嘗試順序參數，讓它能夠使用 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="bcbb2-171">**✓ CONSIDER** 小極為重視效能的應用程式開發介面中的引數數目的呼叫中提供特殊的多載，程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="bcbb2-172">如此一來，當使用少數引數呼叫 API 時，就可以避免建立陣列物件。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="bcbb2-173">藉由取得陣列參數的單數形式並加上數值後置詞，來形成參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="bcbb2-174">只有在您要特別使用整個程式碼路徑時，才應該這麼做，而不只是建立陣列並呼叫更通用的方法。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="bcbb2-175">**✓ DO** 注意可以當成參數陣列引數傳遞的 null。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="bcbb2-176">在處理之前，您應該先驗證陣列不是 null。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="bcbb2-177">**X DO NOT** 使用 `varargs` 方法，否則會以省略符號。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="bcbb2-178">某些 CLR 語言（例如C++）支援傳遞變數參數清單的替代慣例，稱為 @no__t 1 方法。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="bcbb2-179">慣例不應用於架構中，因為它不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="bcbb2-180">指標參數</span><span class="sxs-lookup"><span data-stu-id="bcbb2-180">Pointer Parameters</span></span>  
 <span data-ttu-id="bcbb2-181">一般而言，指標不應該出現在設計良好的 managed 程式碼架構的公用介面區中。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="bcbb2-182">在大部分的情況下，都應該封裝指標。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="bcbb2-183">不過，在某些情況下，指標是基於互通性的原因，而在這種情況下使用指標是適當的。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="bcbb2-184">**✓ DO** 適用於任何會使用指標引數的成員提供的替代方案，因為不符合 CLS 標準的指標。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="bcbb2-185">**X AVOID** 執行耗費資源檢查指標引數的引數。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="bcbb2-186">**✓ DO** 設計具有指標的成員時，請遵循一般指標相關的慣例。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="bcbb2-187">例如，不需要傳遞開始索引，因為可以使用簡單的指標算術來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="bcbb2-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="bcbb2-188">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="bcbb2-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bcbb2-189">從 @no__t 1Framework 設計指導方針中，@no__t 0Reprinted by 皮耳森教育，Inc. 的許可權：可重複使用的 .NET 程式庫、第2版 @ no__t-0 by Krzysztof Cwalina 和 Brad Abrams 的慣例、慣用語和模式，已于2008年10月22日發行，其為 Microsoft Windows 開發系列的一部分 Addison-Wesley Professional。 \*</span><span class="sxs-lookup"><span data-stu-id="bcbb2-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcbb2-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcbb2-190">See also</span></span>

- [<span data-ttu-id="bcbb2-191">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="bcbb2-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="bcbb2-192">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="bcbb2-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
