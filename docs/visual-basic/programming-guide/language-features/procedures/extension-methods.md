---
title: "擴充方法 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d3db3bc2b213b78ef2dceebcf56c9d5fbfa3016e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="9e5e7-102">擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e5e7-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="9e5e7-103">擴充方法可讓開發人員將自訂功能加入至已定義而不需要建立新的衍生的類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="9e5e7-104">擴充方法可讓撰寫方法，這個方法，就好像現有類型的執行個體方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e5e7-105">備註</span><span class="sxs-lookup"><span data-stu-id="9e5e7-105">Remarks</span></span>  
 <span data-ttu-id="9e5e7-106">擴充方法可以只`Sub`程序或`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="9e5e7-107">您無法定義延伸模組屬性、 欄位或事件。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="9e5e7-108">所有擴充方法必須標示都為使用擴充屬性`<Extension()>`從<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="9e5e7-109">擴充方法定義中的第一個參數指定方法可擴充的資料類型。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="9e5e7-110">當方法執行時，第一個參數是繫結至叫用方法的資料類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e5e7-111">範例</span><span class="sxs-lookup"><span data-stu-id="9e5e7-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9e5e7-112">描述</span><span class="sxs-lookup"><span data-stu-id="9e5e7-112">Description</span></span>  
 <span data-ttu-id="9e5e7-113">下列範例會定義`Print`延伸<xref:System.String>資料型別。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="9e5e7-114">此方法會使用`Console.WriteLine`顯示字串。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="9e5e7-115">參數`Print`方法， `aString`，建立方法可擴充<xref:System.String>類別。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 <span data-ttu-id="9e5e7-116">請注意，標記為使用擴充屬性的擴充方法定義`<Extension()>`。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-116">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="9e5e7-117">將標示方法定義的模組是選擇性的但必須標記每個擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-117">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="9e5e7-118"><xref:System.Runtime.CompilerServices>必須先匯入，才能存取此延伸模組屬性。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-118"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="9e5e7-119">擴充方法可以只在模組內宣告。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-119">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="9e5e7-120">一般而言，擴充方法定義所在的模組不是相同的模組呼叫它的一個。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-120">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="9e5e7-121">相反地，包含擴充方法的模組匯入時，如果它必須是，若要將它帶到範圍。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-121">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="9e5e7-122">包含的模組之後`Print`是在範圍內，呼叫此方法可以如同一般的執行個體方法，不接受引數，例如`ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="9e5e7-122">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 <span data-ttu-id="9e5e7-123">下一個範例中， `PrintAndPunctuate`，也是延伸<xref:System.String>，這次定義具有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-123">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="9e5e7-124">第一個參數， `aString`，建立擴充方法，延伸<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-124">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="9e5e7-125">第二個參數， `punc`，要用的字串時，會傳遞做為引數呼叫該方法的標點符號。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-125">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="9e5e7-126">此方法會顯示後面的標點符號的字串。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-126">The method displays the string followed by the punctuation marks.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 <span data-ttu-id="9e5e7-127">傳送中的字串引數呼叫的方法`punc`:`example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="9e5e7-127">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="9e5e7-128">下列範例所示`Print`和`PrintAndPunctuate`定義和呼叫。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-128">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="9e5e7-129"><xref:System.Runtime.CompilerServices>在匯入定義模組以啟用擴充功能屬性的存取權。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-129"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9e5e7-130">程式碼</span><span class="sxs-lookup"><span data-stu-id="9e5e7-130">Code</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="9e5e7-131">接下來，擴充方法帶入範圍，而且呼叫。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-131">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="9e5e7-132">註解</span><span class="sxs-lookup"><span data-stu-id="9e5e7-132">Comments</span></span>  
 <span data-ttu-id="9e5e7-133">所有，並在需要能夠執行這些或類似的擴充方法是它們是在範圍內。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="9e5e7-134">如果在範圍內包含的擴充方法的模組，它會顯示在 IntelliSense 中，並可以如同一般的執行個體方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="9e5e7-135">請注意，方法會叫用時，未傳送引數第一個參數。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="9e5e7-136">參數`aString`在上一個方法定義為繫結至`example`，執行個體`String`呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="9e5e7-137">編譯器將使用`example`為傳送至第一個參數的引數。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="9e5e7-138">如果設為物件呼叫擴充方法`Nothing`，擴充方法會執行。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="9e5e7-139">這不適用於一般的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="9e5e7-140">您可以明確檢查是否有`Nothing`中擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-140">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="9e5e7-141">可延伸的型別</span><span class="sxs-lookup"><span data-stu-id="9e5e7-141">Types That Can Be Extended</span></span>  
 <span data-ttu-id="9e5e7-142">您可以定義擴充方法的大部分型別可以用來表示 Visual Basic 的參數清單，包括下列：</span><span class="sxs-lookup"><span data-stu-id="9e5e7-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="9e5e7-143">類別 （參考類型）</span><span class="sxs-lookup"><span data-stu-id="9e5e7-143">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="9e5e7-144">結構 （實值類型）</span><span class="sxs-lookup"><span data-stu-id="9e5e7-144">Structures (value types)</span></span>  
  
-   <span data-ttu-id="9e5e7-145">介面</span><span class="sxs-lookup"><span data-stu-id="9e5e7-145">Interfaces</span></span>  
  
-   <span data-ttu-id="9e5e7-146">委派</span><span class="sxs-lookup"><span data-stu-id="9e5e7-146">Delegates</span></span>  
  
-   <span data-ttu-id="9e5e7-147">ByRef 和 ByVal 引數</span><span class="sxs-lookup"><span data-stu-id="9e5e7-147">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="9e5e7-148">泛型方法的參數</span><span class="sxs-lookup"><span data-stu-id="9e5e7-148">Generic method parameters</span></span>  
  
-   <span data-ttu-id="9e5e7-149">陣列</span><span class="sxs-lookup"><span data-stu-id="9e5e7-149">Arrays</span></span>  
  
 <span data-ttu-id="9e5e7-150">第一個參數會指定擴充方法所擴充的資料類型，因為它需要而不得為選用。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="9e5e7-151">基於這個原因，`Optional`參數和`ParamArray`參數不可以是參數清單中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="9e5e7-152">擴充方法不會視為在晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="9e5e7-153">在下列範例中，陳述式`anObject.PrintMe()`引發<xref:System.MissingMemberException>例外狀況，如果您會看到相同的例外狀況，第二個`PrintMe`擴充方法定義已刪除。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a><span data-ttu-id="9e5e7-154">最佳作法</span><span class="sxs-lookup"><span data-stu-id="9e5e7-154">Best Practices</span></span>  
 <span data-ttu-id="9e5e7-155">擴充方法提供方便且功能強大的方式，來擴充現有的類型。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="9e5e7-156">不過，若要順利使用，有一些要考慮的事項。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="9e5e7-157">這些考量主要適用於類別庫的作者，但它們可能會影響使用擴充方法的任何應用程式。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="9e5e7-158">一般來說，您將加入至您並未擁有的型別的擴充方法是擴充方法新增至您所控制的型別比更容易遭受的。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="9e5e7-159">有許多種，可能會發生在您並未擁有的類別可能會干擾您的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="9e5e7-160">有任何可存取的執行個體成員具有所需的引數至參數沒有縮小轉換中呼叫的陳述式的引數與相容的簽章，執行個體方法會使用任何擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="9e5e7-161">因此，在某個時間點的類別加入適當的執行個體方法，如果您依賴的現有擴充成員可能會無法存取。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="9e5e7-162">擴充方法的作者無法防止其他程式設計師撰寫衝突可能高於原始副檔名的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="9e5e7-163">您可以將擴充方法放在自己的命名空間中改善健全性。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="9e5e7-164">您的程式庫的取用者可以再命名空間或包含或排除它，在命名空間，分開其餘的程式庫之中選取。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="9e5e7-165">它可能、 更安全地擴充介面，而不是擴充類別，尤其是如果您並未擁有介面或類別。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="9e5e7-166">在介面中的變更會影響實作它的每個類別。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="9e5e7-167">因此，作者可能會比較容易新增或變更介面中的方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="9e5e7-168">不過，如果類別實作相同的簽章的擴充方法的兩個介面，會顯示這兩種擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="9e5e7-169">延伸您可以最特定的型別。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-169">Extend the most specific type you can.</span></span> <span data-ttu-id="9e5e7-170">在階層中的型別，如果您選取要從中衍生許多其他類型，類型有圖層的執行個體方法或其他可能會干擾您的擴充方法的簡介的可能性。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="9e5e7-171">擴充方法、 執行個體方法和屬性</span><span class="sxs-lookup"><span data-stu-id="9e5e7-171">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="9e5e7-172">是呼叫陳述式的引數與相容的簽章的範圍內執行個體方法時，執行個體方法是選擇任何擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="9e5e7-173">執行個體方法具有優先順序，即使此擴充方法是較佳的相符項目。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="9e5e7-174">在下列範例中，`ExampleClass`包含名為的執行個體方法`ExampleMethod`具有型別的一個參數`Integer`。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="9e5e7-175">擴充方法`ExampleMethod`擴充`ExampleClass`，且具有一個參數的型別`Long`。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 <span data-ttu-id="9e5e7-176">第一次呼叫`ExampleMethod`在下列程式碼會呼叫擴充方法，因為`arg1`是`Long`和僅與相容`Long`中擴充方法的參數。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="9e5e7-177">第二個呼叫`ExampleMethod`具有`Integer`引數， `arg2`，而且它會呼叫執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 <span data-ttu-id="9e5e7-178">現在反向兩個方法中參數的資料的類型：</span><span class="sxs-lookup"><span data-stu-id="9e5e7-178">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 <span data-ttu-id="9e5e7-179">這次中的程式碼`Main`呼叫的執行個體方法兩次。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="9e5e7-180">這是因為同時`arg1`和`arg2`能夠擴展轉換成`Long`，和執行個體方法的優先順序高於在這兩種情況下擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 <span data-ttu-id="9e5e7-181">因此，擴充方法無法取代現有的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="9e5e7-182">不過，當擴充方法的執行個體方法名稱相同，但簽章不發生衝突，可以存取這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="9e5e7-183">例如，如果類別`ExampleClass`包含方法，名為`ExampleMethod`採用任何引數，具有相同名稱的擴充方法，但允許不同的簽章，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 <span data-ttu-id="9e5e7-184">此程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e5e7-184">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="9e5e7-185">這種情況是簡單屬性： 如果擴充方法具有相同屬性的名稱相同的類別，它會擴充，擴充方法不可見，且無法存取。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="9e5e7-186">擴充方法優先順序</span><span class="sxs-lookup"><span data-stu-id="9e5e7-186">Extension Method Precedence</span></span>  
 <span data-ttu-id="9e5e7-187">兩個具有相同的簽章的擴充方法是在範圍內，而且可存取，則具有較高的優先順序會叫用。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="9e5e7-188">擴充方法的優先順序根據用來將方法帶到範圍的機制。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="9e5e7-189">下列清單顯示優先順序階層中的，從最高到最低。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1.  <span data-ttu-id="9e5e7-190">目前的模組內定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-190">Extension methods defined inside the current module.</span></span>  
  
2.  <span data-ttu-id="9e5e7-191">擴充方法定義內的資料類型在目前命名空間，或其父代的任何一個的優先順序高於父命名空間的子命名空間。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3.  <span data-ttu-id="9e5e7-192">任何型別中的匯入目前的檔案內定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-192">Extension methods defined inside any type imports in the current file.</span></span>  
  
4.  <span data-ttu-id="9e5e7-193">在任何命名空間中的匯入目前的檔案內定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-193">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5.  <span data-ttu-id="9e5e7-194">任何專案層級類型匯入定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-194">Extension methods defined inside any project-level type imports.</span></span>  
  
6.  <span data-ttu-id="9e5e7-195">任何專案層級命名空間匯入定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-195">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="9e5e7-196">如果優先順序無法解決模稜兩可，您可以使用完整限定的名稱來指定您要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="9e5e7-197">如果`Print`前面範例中的方法定義中名為`StringExtensions`，完整的名稱是`StringExtensions.Print(example)`而不是`example.Print()`。</span><span class="sxs-lookup"><span data-stu-id="9e5e7-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5e7-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e5e7-198">See Also</span></span>  
 <xref:System.Runtime.CompilerServices>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="9e5e7-199">擴充方法</span><span class="sxs-lookup"><span data-stu-id="9e5e7-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [<span data-ttu-id="9e5e7-200">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="9e5e7-200">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="9e5e7-201">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="9e5e7-201">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="9e5e7-202">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="9e5e7-202">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="9e5e7-203">參數陣列</span><span class="sxs-lookup"><span data-stu-id="9e5e7-203">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="9e5e7-204">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="9e5e7-204">Attributes overview</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="9e5e7-205">在 Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="9e5e7-205">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
