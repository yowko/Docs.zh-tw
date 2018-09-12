---
title: 參數設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5311de8cef266af23b259d943568bfa95eaf72
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44493923"
---
# <a name="parameter-design"></a><span data-ttu-id="28d54-102">參數設計</span><span class="sxs-lookup"><span data-stu-id="28d54-102">Parameter Design</span></span>
<span data-ttu-id="28d54-103">本章節會提供廣泛的指導方針，在參數的設計，包括各節來檢查引數的指導方針。</span><span class="sxs-lookup"><span data-stu-id="28d54-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="28d54-104">此外，您應該參閱中所述的指導方針[命名的參數](../../../docs/standard/design-guidelines/naming-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="28d54-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="28d54-105">**✓ DO** 使用至少衍生的參數類型，提供成員所需的功能。</span><span class="sxs-lookup"><span data-stu-id="28d54-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="28d54-106">例如，假設您想要設計的方法，列舉集合，並會列印到主控台的每個項目。</span><span class="sxs-lookup"><span data-stu-id="28d54-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="28d54-107">這種方法花費<xref:System.Collections.IEnumerable>做為參數，不<xref:System.Collections.ArrayList>或<xref:System.Collections.IList>，例如。</span><span class="sxs-lookup"><span data-stu-id="28d54-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="28d54-108">**X DO NOT** 使用保留的參數。</span><span class="sxs-lookup"><span data-stu-id="28d54-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="28d54-109">如果某些未來的版本中需要更多輸入才能成員，就可以加入新的多載。</span><span class="sxs-lookup"><span data-stu-id="28d54-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="28d54-110">**X DO NOT** 有公開這些方法會採用指標、 陣列的指標或做為參數的多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="28d54-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="28d54-111">指標和多維度陣列是相對較難適當地使用。</span><span class="sxs-lookup"><span data-stu-id="28d54-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="28d54-112">在幾乎所有的情況下，就可以重新設計 Api 避免這些類型做為參數。</span><span class="sxs-lookup"><span data-stu-id="28d54-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="28d54-113">**✓ DO** 放置所有 `out` 遵循所有由值參數和 `ref` 參數 （不含參數陣列），即使它會造成不一致的參數多載之間的順序 (請參閱 [成員多載 ](../../../docs/standard/design-guidelines/member-overloading.md))。</span><span class="sxs-lookup"><span data-stu-id="28d54-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="28d54-114">`out`參數可視為額外的傳回值，並將它們群組在一起會更容易了解的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="28d54-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="28d54-115">**✓ DO** 一致時覆寫成員命名的參數，或實作介面成員中。</span><span class="sxs-lookup"><span data-stu-id="28d54-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="28d54-116">這會進一步通訊方法之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="28d54-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="28d54-117">選擇列舉或布林值參數</span><span class="sxs-lookup"><span data-stu-id="28d54-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="28d54-118">**✓ DO** 如果成員原本必須另外兩個或多個布林值參數使用的列舉。</span><span class="sxs-lookup"><span data-stu-id="28d54-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="28d54-119">**X DO NOT** 使用布林值，除非您完全確定永遠不會需要兩個以上的值。</span><span class="sxs-lookup"><span data-stu-id="28d54-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="28d54-120">列舉會提供一些的空間，以便未來加入值，但是您應該注意將值加入至列舉中所述的所有的含意[列舉設計](../../../docs/standard/design-guidelines/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="28d54-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="28d54-121">**✓ CONSIDER** 使用建構函式參數是真正的兩個狀態的值，只會用來初始化布林值屬性的布林值。</span><span class="sxs-lookup"><span data-stu-id="28d54-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="28d54-122">驗證引數</span><span class="sxs-lookup"><span data-stu-id="28d54-122">Validating Arguments</span></span>  
 <span data-ttu-id="28d54-123">**✓ DO** 驗證引數傳遞至 public、 protected 或明確實作的成員。</span><span class="sxs-lookup"><span data-stu-id="28d54-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="28d54-124">擲回<xref:System.ArgumentException?displayProperty=nameWithType>，或其中一個子類別，如果驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="28d54-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="28d54-125">請注意，實際的驗證不一定要在公用或受保護成員本身中。</span><span class="sxs-lookup"><span data-stu-id="28d54-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="28d54-126">它可能會發生一些私用或內部的常式中較低層級。</span><span class="sxs-lookup"><span data-stu-id="28d54-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="28d54-127">主要的重點是公開給使用者的整個介面區檢查引數。</span><span class="sxs-lookup"><span data-stu-id="28d54-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="28d54-128">**✓ DO** 擲回 <xref:System.ArgumentNullException> 如果傳遞 null 引數，而且成員不支援 null 引數。</span><span class="sxs-lookup"><span data-stu-id="28d54-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="28d54-129">**✓ DO** 驗證列舉的參數。</span><span class="sxs-lookup"><span data-stu-id="28d54-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="28d54-130">請勿假設列舉引數會在列舉所定義的範圍。</span><span class="sxs-lookup"><span data-stu-id="28d54-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="28d54-131">CLR 可讓轉換任何整數值轉換為列舉值，即使值未定義的列舉中。</span><span class="sxs-lookup"><span data-stu-id="28d54-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="28d54-132">**X DO NOT** 使用 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 列舉範圍檢查。</span><span class="sxs-lookup"><span data-stu-id="28d54-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="28d54-133">**✓ DO** 注意之後他們已驗證，可能已經變更可變動的引數。</span><span class="sxs-lookup"><span data-stu-id="28d54-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="28d54-134">如果成員是機密的安全性，即建議來建立複本，然後驗證和處理引數。</span><span class="sxs-lookup"><span data-stu-id="28d54-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="28d54-135">參數傳遞</span><span class="sxs-lookup"><span data-stu-id="28d54-135">Parameter Passing</span></span>  
 <span data-ttu-id="28d54-136">從架構設計師的觀點來看，有三個參數的主要群組： 藉由值參數`ref`參數，和`out`參數。</span><span class="sxs-lookup"><span data-stu-id="28d54-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="28d54-137">透過傳值參數傳遞的引數時，該成員就會收到一份在傳遞的實際引數。</span><span class="sxs-lookup"><span data-stu-id="28d54-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="28d54-138">如果引數是實值型別，會將引數的複本放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="28d54-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="28d54-139">如果引數是參考型別，參考的複本放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="28d54-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="28d54-140">最受歡迎 CLR 語言，例如 C#、 VB.NET 和 c + +，以傳值方式傳遞參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="28d54-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="28d54-141">引數傳遞時`ref`參數，該成員收到傳入的實質引數的參考。</span><span class="sxs-lookup"><span data-stu-id="28d54-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="28d54-142">引數是實值型別，引數的參考會放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="28d54-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="28d54-143">引數是參考型別，參考的參考會放在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="28d54-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="28d54-144">`Ref` 參數可用來允許修改由呼叫端傳遞的引數的成員。</span><span class="sxs-lookup"><span data-stu-id="28d54-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="28d54-145">`Out` 參數是類似於`ref`參數，但有一些小差異。</span><span class="sxs-lookup"><span data-stu-id="28d54-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="28d54-146">參數一開始被視為未設定，並且無法在指派一些值之前讀取成員主體中。</span><span class="sxs-lookup"><span data-stu-id="28d54-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="28d54-147">此外，參數有成員傳回之前指派一些值。</span><span class="sxs-lookup"><span data-stu-id="28d54-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="28d54-148">**X AVOID** 使用 `out` 或 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="28d54-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="28d54-149">使用`out`或`ref`參數需要經驗指標了實值型別和參考型別之間的差異，並處理具有多個傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="28d54-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="28d54-150">此外，之間的差異`out`和`ref`參數不廣泛了解。</span><span class="sxs-lookup"><span data-stu-id="28d54-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="28d54-151">Framework 設計適合一般觀眾的架構設計人員不應該預期使用者會熟練地運用`out`或`ref`參數。</span><span class="sxs-lookup"><span data-stu-id="28d54-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="28d54-152">**X DO NOT** 傳址方式傳遞參考型別。</span><span class="sxs-lookup"><span data-stu-id="28d54-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="28d54-153">有一些規則，例如可以用來交換參考方法的有限例外狀況。</span><span class="sxs-lookup"><span data-stu-id="28d54-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="28d54-154">使用變動數目的參數的成員</span><span class="sxs-lookup"><span data-stu-id="28d54-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="28d54-155">可以接受可變數目的引數的成員會藉由提供的陣列參數來表示。</span><span class="sxs-lookup"><span data-stu-id="28d54-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="28d54-156">比方說，<xref:System.String>提供下列方法：</span><span class="sxs-lookup"><span data-stu-id="28d54-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="28d54-157">使用者接著可以呼叫<xref:System.String.Format%2A?displayProperty=nameWithType>方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="28d54-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="28d54-158">加入的陣列參數中的 C# params 關鍵字對所謂的 params 陣列參數中的參數，並提供捷徑，以建立暫存陣列。</span><span class="sxs-lookup"><span data-stu-id="28d54-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="28d54-159">如此一來，可讓使用者藉由傳遞陣列元素的引數清單中的直接呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="28d54-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="28d54-160">請注意，params 關鍵字可以只能加入至參數清單中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="28d54-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="28d54-161">**✓ CONSIDER** params 關鍵字加入陣列參數，如果您預期使用者會傳遞具有少數的元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="28d54-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="28d54-162">如果預期的許多項目將會收到在一般案例，使用者，可能無法通過這些內嵌的項目，因此不需要 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="28d54-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="28d54-163">**X AVOID** 使用參數陣列，如果呼叫端會幾乎都已經輸入陣列中。</span><span class="sxs-lookup"><span data-stu-id="28d54-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="28d54-164">比方說，成員使用位元組陣列參數幾乎不會呼叫傳遞個別的位元組。</span><span class="sxs-lookup"><span data-stu-id="28d54-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="28d54-165">基於這個理由，在.NET Framework 中的位元組陣列參數請勿使用 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="28d54-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="28d54-166">**X DO NOT** 使用參數陣列，如果陣列修改採取 params 陣列參數的成員。</span><span class="sxs-lookup"><span data-stu-id="28d54-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="28d54-167">事實上，許多編譯器會將該成員的引數轉換成暫存陣列呼叫位置，因為陣列可能是暫存物件，，因此陣列的任何修改可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="28d54-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="28d54-168">**✓ CONSIDER** 使用 params 關鍵字，在簡單的多載中，即使有更複雜的多載無法使用。</span><span class="sxs-lookup"><span data-stu-id="28d54-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="28d54-169">問問自己的使用者會有參數陣列中其中一個多載，即使它不是在所有多載來值。</span><span class="sxs-lookup"><span data-stu-id="28d54-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="28d54-170">**✓ DO** 嘗試順序參數，讓它能夠使用 params 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="28d54-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="28d54-171">**✓ CONSIDER** 小極為重視效能的應用程式開發介面中的引數數目的呼叫中提供特殊的多載，程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="28d54-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="28d54-172">如此可避免使用少量的引數呼叫 API 時，建立陣列物件。</span><span class="sxs-lookup"><span data-stu-id="28d54-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="28d54-173">將陣列參數的單數形式，並將數值後置詞，以形成參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="28d54-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="28d54-174">您應該只能這麼想以特殊案例的完整程式碼路徑，不只是建立陣列，並呼叫的較通用的方法。</span><span class="sxs-lookup"><span data-stu-id="28d54-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="28d54-175">**✓ DO** 注意可以當成參數陣列引數傳遞的 null。</span><span class="sxs-lookup"><span data-stu-id="28d54-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="28d54-176">您應該驗證陣列不是 null 處理之前。</span><span class="sxs-lookup"><span data-stu-id="28d54-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="28d54-177">**X DO NOT** 使用 `varargs` 方法，否則會以省略符號。</span><span class="sxs-lookup"><span data-stu-id="28d54-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="28d54-178">某些 CLR 語言，例如 c + + 支援替代的慣例來傳遞呼叫的變數參數清單`varargs`方法。</span><span class="sxs-lookup"><span data-stu-id="28d54-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="28d54-179">慣例不應在架構，因為它不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="28d54-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="28d54-180">指標參數</span><span class="sxs-lookup"><span data-stu-id="28d54-180">Pointer Parameters</span></span>  
 <span data-ttu-id="28d54-181">一般情況下，指標不應該出現在設計良好的 managed 程式碼架構的公用表面區域。</span><span class="sxs-lookup"><span data-stu-id="28d54-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="28d54-182">大部分的情況下，應該封裝的指標。</span><span class="sxs-lookup"><span data-stu-id="28d54-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="28d54-183">不過，在某些情況下，指標所需的互通性考量，並且適合在此情況下使用指標。</span><span class="sxs-lookup"><span data-stu-id="28d54-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="28d54-184">**✓ DO** 適用於任何會使用指標引數的成員提供的替代方案，因為不符合 CLS 標準的指標。</span><span class="sxs-lookup"><span data-stu-id="28d54-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="28d54-185">**X AVOID** 執行耗費資源檢查指標引數的引數。</span><span class="sxs-lookup"><span data-stu-id="28d54-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="28d54-186">**✓ DO** 設計具有指標的成員時，請遵循一般指標相關的慣例。</span><span class="sxs-lookup"><span data-stu-id="28d54-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="28d54-187">比方說，沒有必要將起始的索引，因為可以使用簡單指標算術來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="28d54-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="28d54-188">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="28d54-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="28d54-189">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="28d54-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d54-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28d54-190">See also</span></span>

- [<span data-ttu-id="28d54-191">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="28d54-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="28d54-192">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="28d54-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
