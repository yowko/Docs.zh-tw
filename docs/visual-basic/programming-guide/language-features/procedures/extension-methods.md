---
title: 擴充方法 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: b5ad066fe9ec40d715702ed99537f45b21c558cf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701047"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="5c39a-102">擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c39a-102">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="5c39a-103">擴充方法可讓開發人員將自訂功能加入至已定義的資料類型，而不需要建立新的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="5c39a-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="5c39a-104">擴充方法可讓您撰寫方法，如同現有類型的實例方法一樣，可以呼叫它。</span><span class="sxs-lookup"><span data-stu-id="5c39a-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="5c39a-105">備註</span><span class="sxs-lookup"><span data-stu-id="5c39a-105">Remarks</span></span>

<span data-ttu-id="5c39a-106">擴充方法只能是 @no__t 0 程式或 @no__t 1 程式。</span><span class="sxs-lookup"><span data-stu-id="5c39a-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="5c39a-107">您不能定義擴充屬性、欄位或事件。</span><span class="sxs-lookup"><span data-stu-id="5c39a-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="5c39a-108">所有擴充方法都必須以 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中的擴充屬性 `<Extension>` 標記，而且必須在[模組](../../../language-reference/statements/module-statement.md)中定義。</span><span class="sxs-lookup"><span data-stu-id="5c39a-108">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="5c39a-109">如果在模組外部定義擴充方法，Visual Basic 編譯器會產生錯誤[BC36551](../../../misc/bc36551.md)「擴充方法只能在模組中定義」。</span><span class="sxs-lookup"><span data-stu-id="5c39a-109">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="5c39a-110">擴充方法定義中的第一個參數會指定方法擴充的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5c39a-110">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="5c39a-111">當執行方法時，第一個參數會系結至叫用方法之資料類型的實例。</span><span class="sxs-lookup"><span data-stu-id="5c39a-111">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="5c39a-112">@No__t-0 屬性只能套用至 Visual Basic [`Module`](../../../language-reference/statements/module-statement.md)、 [`Sub`](../../../language-reference/statements/sub-statement.md)或[`Function`](../../../language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5c39a-112">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="5c39a-113">如果您將它套用至 `Class` 或 `Structure`，則 Visual Basic 編譯器會產生錯誤[BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md)，"Extension ' 屬性只能套用到 ' Module '、' Sub ' 或 ' Function ' 宣告。</span><span class="sxs-lookup"><span data-stu-id="5c39a-113">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="5c39a-114">範例</span><span class="sxs-lookup"><span data-stu-id="5c39a-114">Example</span></span>

<span data-ttu-id="5c39a-115">下列範例會定義 <xref:System.String> 資料類型的 `Print` 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5c39a-115">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="5c39a-116">方法會使用 `Console.WriteLine` 來顯示字串。</span><span class="sxs-lookup"><span data-stu-id="5c39a-116">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="5c39a-117">@No__t-0 方法的參數（`aString`）會建立方法擴充 @no__t 2 類別。</span><span class="sxs-lookup"><span data-stu-id="5c39a-117">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>
  
[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="5c39a-118">請注意，擴充方法定義已標記 `<Extension()>` 的延伸模組屬性。</span><span class="sxs-lookup"><span data-stu-id="5c39a-118">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="5c39a-119">標記方法定義所在的模組是選擇性的，但每個擴充方法都必須標記為。</span><span class="sxs-lookup"><span data-stu-id="5c39a-119">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="5c39a-120">必須匯入 <xref:System.Runtime.CompilerServices>，才能存取擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="5c39a-120"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="5c39a-121">擴充方法只能在模組內宣告。</span><span class="sxs-lookup"><span data-stu-id="5c39a-121">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="5c39a-122">一般而言，在其中定義擴充方法的模組，與呼叫它的模組不同。</span><span class="sxs-lookup"><span data-stu-id="5c39a-122">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="5c39a-123">相反地，會匯入包含擴充方法的模組（如果需要的話），使其成為範圍。</span><span class="sxs-lookup"><span data-stu-id="5c39a-123">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="5c39a-124">在包含 `Print` 的模組位於範圍內之後，就可以呼叫方法，就像是不採用任何引數的一般實例方法，例如 `ToUpper`：</span><span class="sxs-lookup"><span data-stu-id="5c39a-124">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="5c39a-125">下一個範例 `PrintAndPunctuate`，也是 <xref:System.String> 的延伸模組，這次是以兩個參數定義。</span><span class="sxs-lookup"><span data-stu-id="5c39a-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="5c39a-126">第一個參數 `aString`，會建立擴充方法擴充 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="5c39a-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="5c39a-127">第二個參數 `punc`，其目的是在呼叫方法時當做引數傳入的標點符號字串。</span><span class="sxs-lookup"><span data-stu-id="5c39a-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="5c39a-128">方法會顯示後面接著標點符號的字串。</span><span class="sxs-lookup"><span data-stu-id="5c39a-128">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="5c39a-129">方法的呼叫方式是傳送 `punc` 的字串引數： `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="5c39a-129">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="5c39a-130">下列範例會顯示已定義和呼叫 `Print` 和 @no__t 1。</span><span class="sxs-lookup"><span data-stu-id="5c39a-130">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="5c39a-131"><xref:System.Runtime.CompilerServices> 會匯入定義模組中，以便啟用擴充屬性的存取。</span><span class="sxs-lookup"><span data-stu-id="5c39a-131"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>


```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="5c39a-132">接下來，擴充方法會帶入範圍並呼叫：</span><span class="sxs-lookup"><span data-stu-id="5c39a-132">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="5c39a-133">能夠執行這些或類似的擴充方法所需的一切，都是在範圍內。</span><span class="sxs-lookup"><span data-stu-id="5c39a-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="5c39a-134">如果包含擴充方法的模組在範圍內，它會顯示在 IntelliSense 中，而且可以如同一般實例方法一樣呼叫。</span><span class="sxs-lookup"><span data-stu-id="5c39a-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="5c39a-135">請注意，當叫用方法時，不會在中針對第一個參數傳送任何引數。</span><span class="sxs-lookup"><span data-stu-id="5c39a-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="5c39a-136">先前方法定義中的參數 `aString` 系結至 `example`，也就是呼叫它們的 @no__t 的實例。</span><span class="sxs-lookup"><span data-stu-id="5c39a-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="5c39a-137">編譯器會使用 `example` 做為傳送至第一個參數的引數。</span><span class="sxs-lookup"><span data-stu-id="5c39a-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="5c39a-138">如果針對設定為 `Nothing` 的物件呼叫擴充方法，則會執行擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="5c39a-139">這並不適用于一般實例方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="5c39a-140">您可以明確地檢查擴充方法中的 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="5c39a-140">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="5c39a-141">可以擴充的類型</span><span class="sxs-lookup"><span data-stu-id="5c39a-141">Types that can be extended</span></span>

<span data-ttu-id="5c39a-142">您可以在可在 Visual Basic 參數清單中表示的大部分類型上定義擴充方法，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="5c39a-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="5c39a-143">類別（參考型別）</span><span class="sxs-lookup"><span data-stu-id="5c39a-143">Classes (reference types)</span></span>
- <span data-ttu-id="5c39a-144">結構（實數值型別）</span><span class="sxs-lookup"><span data-stu-id="5c39a-144">Structures (value types)</span></span>
- <span data-ttu-id="5c39a-145">介面</span><span class="sxs-lookup"><span data-stu-id="5c39a-145">Interfaces</span></span>
- <span data-ttu-id="5c39a-146">委派</span><span class="sxs-lookup"><span data-stu-id="5c39a-146">Delegates</span></span>
- <span data-ttu-id="5c39a-147">ByRef 和 ByVal 引數</span><span class="sxs-lookup"><span data-stu-id="5c39a-147">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="5c39a-148">泛型方法參數</span><span class="sxs-lookup"><span data-stu-id="5c39a-148">Generic method parameters</span></span>
- <span data-ttu-id="5c39a-149">陣列</span><span class="sxs-lookup"><span data-stu-id="5c39a-149">Arrays</span></span>

<span data-ttu-id="5c39a-150">因為第一個參數指定擴充方法所擴充的資料類型，所以它是必要的，而且不能是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5c39a-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="5c39a-151">基於這個理由，`Optional` 參數和 @no__t 1 參數不可以是參數清單中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="5c39a-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="5c39a-152">延伸方法不會被視為晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="5c39a-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="5c39a-153">在下列範例中，`anObject.PrintMe()` 的語句會引發 <xref:System.MissingMemberException> 例外狀況，這是您在第二個 `PrintMe` 擴充方法定義已刪除時所看到的相同例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5c39a-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="5c39a-154">最佳做法</span><span class="sxs-lookup"><span data-stu-id="5c39a-154">Best practices</span></span>

<span data-ttu-id="5c39a-155">擴充方法提供了一個方便且功能強大的方式來擴充現有的類型。</span><span class="sxs-lookup"><span data-stu-id="5c39a-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="5c39a-156">不過，若要成功使用它們，有一些重點需要考慮。</span><span class="sxs-lookup"><span data-stu-id="5c39a-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="5c39a-157">這些考慮主要適用于類別庫的作者，但它們可能會影響任何使用擴充方法的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c39a-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="5c39a-158">最常見的情況是，您新增至您未擁有之類型的擴充方法，會比新增至您所控制之類型的擴充方法更容易受到攻擊。</span><span class="sxs-lookup"><span data-stu-id="5c39a-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="5c39a-159">您不擁有的類別可能會發生一些問題，這可能會干擾您的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="5c39a-160">如果有任何可存取的實例成員存在，且其簽章與呼叫語句中的引數相容，而且引數至參數不需要任何縮小轉換，則實例方法將會在任何擴充方法的喜好設定中使用。</span><span class="sxs-lookup"><span data-stu-id="5c39a-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="5c39a-161">因此，如果在某個時間點將適當的實例方法加入至類別，則您依賴的現有延伸模組成員可能會變成無法存取。</span><span class="sxs-lookup"><span data-stu-id="5c39a-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="5c39a-162">擴充方法的作者無法防止其他程式設計人員撰寫衝突的擴充方法，其優先順序可能高於原始的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5c39a-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="5c39a-163">您可以藉由將擴充方法放在自己的命名空間中，來改善穩定性。</span><span class="sxs-lookup"><span data-stu-id="5c39a-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="5c39a-164">您的程式庫取用者可以包含命名空間或將其排除，或在命名空間之間，與程式庫的其餘部分分開。</span><span class="sxs-lookup"><span data-stu-id="5c39a-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="5c39a-165">擴充介面可能會比擴充類別更安全，特別是當您沒有擁有介面或類別時。</span><span class="sxs-lookup"><span data-stu-id="5c39a-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="5c39a-166">介面中的變更會影響每個執行它的類別。</span><span class="sxs-lookup"><span data-stu-id="5c39a-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="5c39a-167">因此，作者可能比較不可能在介面中新增或變更方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="5c39a-168">不過，如果類別所執行的兩個介面具有相同簽章的擴充方法，則不會顯示任何擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="5c39a-169">擴充您可以的最特定類型。</span><span class="sxs-lookup"><span data-stu-id="5c39a-169">Extend the most specific type you can.</span></span> <span data-ttu-id="5c39a-170">在類型的階層架構中，如果您選取衍生許多其他類型的類型，可能會有一些層級的導入實例方法或其他可能會干擾您的的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="5c39a-171">擴充方法、實例方法和屬性</span><span class="sxs-lookup"><span data-stu-id="5c39a-171">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="5c39a-172">當範圍內的實例方法具有與呼叫語句的引數相容的簽章時，會將實例方法選擇為任何擴充方法的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="5c39a-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="5c39a-173">即使擴充方法更符合，實例方法仍具有優先權。</span><span class="sxs-lookup"><span data-stu-id="5c39a-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="5c39a-174">在下列範例中，`ExampleClass` 包含名為 `ExampleMethod` 的實例方法，其具有 `Integer` 類型的一個參數。</span><span class="sxs-lookup"><span data-stu-id="5c39a-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="5c39a-175">擴充方法 `ExampleMethod` 會延伸 `ExampleClass`，並具有 `Long` 類型的一個參數。</span><span class="sxs-lookup"><span data-stu-id="5c39a-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="5c39a-176">在下列程式碼中，第一次呼叫 `ExampleMethod` 時，會呼叫擴充方法，因為 `arg1` 是 `Long`，而且僅與擴充方法中的 `Long` 參數相容。</span><span class="sxs-lookup"><span data-stu-id="5c39a-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="5c39a-177">第二次對 `ExampleMethod` 的呼叫具有 `Integer` 引數，`arg2`，而且它會呼叫實例方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="5c39a-178">現在，請在兩個方法中反轉參數的資料類型：</span><span class="sxs-lookup"><span data-stu-id="5c39a-178">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="5c39a-179">這次 @no__t 中的程式碼會呼叫實例方法兩次。</span><span class="sxs-lookup"><span data-stu-id="5c39a-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="5c39a-180">這是因為 `arg1` 和 `arg2` 都有 `Long` 的擴輾轉換，而實例方法的優先順序高於這兩種情況下的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="5c39a-181">因此，擴充方法無法取代現有的實例方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="5c39a-182">不過，當擴充方法的名稱與實例方法相同，但是簽章不衝突時，可以存取這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="5c39a-183">例如，如果類別 `ExampleClass` 包含名為 `ExampleMethod` 且不接受引數的方法，則會允許具有相同名稱但具有不同簽章的擴充方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5c39a-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="5c39a-184">這段程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="5c39a-184">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="5c39a-185">屬性的情況較簡單：如果擴充方法的名稱與它所擴充之類別的屬性相同，則不會顯示擴充方法，而且無法存取。</span><span class="sxs-lookup"><span data-stu-id="5c39a-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="5c39a-186">擴充方法優先順序</span><span class="sxs-lookup"><span data-stu-id="5c39a-186">Extension method precedence</span></span>

<span data-ttu-id="5c39a-187">當具有相同簽章的兩個擴充方法在範圍內且可供存取時，將會叫用具有較高優先順序的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5c39a-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="5c39a-188">擴充方法的優先順序是以用來將方法帶入範圍的機制為基礎。</span><span class="sxs-lookup"><span data-stu-id="5c39a-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="5c39a-189">下列清單顯示優先順序階層，從最高到最低。</span><span class="sxs-lookup"><span data-stu-id="5c39a-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="5c39a-190">在目前模組內定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-190">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="5c39a-191">在目前命名空間中的資料類型或其任何一個父系內定義的擴充方法，其子命名空間的優先順序高於父命名空間。</span><span class="sxs-lookup"><span data-stu-id="5c39a-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="5c39a-192">在目前檔案中的任何類型匯入內定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-192">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="5c39a-193">在目前檔案中的任何命名空間匯入內定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-193">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="5c39a-194">定義于任何專案層級類型匯入內的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-194">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="5c39a-195">在任何專案層級命名空間匯入中定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-195">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="5c39a-196">如果優先順序無法解決不明確的問題，您可以使用完整名稱來指定您要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="5c39a-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="5c39a-197">如果先前範例中的 `Print` 方法是在名為 `StringExtensions` 的模組中定義，則完整名稱會是 `StringExtensions.Print(example)`，而不是 `example.Print()`。</span><span class="sxs-lookup"><span data-stu-id="5c39a-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c39a-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c39a-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="5c39a-199">擴充方法</span><span class="sxs-lookup"><span data-stu-id="5c39a-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="5c39a-200">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="5c39a-200">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="5c39a-201">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="5c39a-201">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5c39a-202">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="5c39a-202">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="5c39a-203">參數陣列</span><span class="sxs-lookup"><span data-stu-id="5c39a-203">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="5c39a-204">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="5c39a-204">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="5c39a-205">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="5c39a-205">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
