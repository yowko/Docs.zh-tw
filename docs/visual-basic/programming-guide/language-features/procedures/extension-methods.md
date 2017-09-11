---
title: "擴充方法 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ExtensionMethods
dev_langs:
- VB
helpviewer_keywords:
- extending data types
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0705929da72bcb3001228a90bbb9d5ba7c248bf7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="6e62d-102">擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e62d-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="6e62d-103">擴充方法可讓開發人員將自訂功能加入到已經不需要建立新的衍生型別定義的資料型別。</span><span class="sxs-lookup"><span data-stu-id="6e62d-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="6e62d-104">擴充方法可讓撰寫方法，就好像現有型別的執行個體方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e62d-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e62d-105">備註</span><span class="sxs-lookup"><span data-stu-id="6e62d-105">Remarks</span></span>  
 <span data-ttu-id="6e62d-106">擴充方法只能是`Sub`程序或`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="6e62d-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="6e62d-107">您無法定義擴充屬性、 欄位或事件。</span><span class="sxs-lookup"><span data-stu-id="6e62d-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="6e62d-108">所有的擴充方法必須標記為延伸屬性`<Extension()>`從<xref:System.Runtime.CompilerServices?displayProperty=fullName>命名空間。</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6e62d-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace.</span></span>  
  
 <span data-ttu-id="6e62d-109">擴充方法定義中的第一個參數會指定方法要擴充的資料型別。</span><span class="sxs-lookup"><span data-stu-id="6e62d-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="6e62d-110">當方法執行時，第一個參數是繫結至叫用方法的資料類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e62d-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e62d-111">範例</span><span class="sxs-lookup"><span data-stu-id="6e62d-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6e62d-112">說明</span><span class="sxs-lookup"><span data-stu-id="6e62d-112">Description</span></span>  
 <span data-ttu-id="6e62d-113">下列範例會定義`Print`延伸<xref:System.String>資料型別。</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6e62d-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="6e62d-114">此方法會使用`Console.WriteLine`顯示字串。</span><span class="sxs-lookup"><span data-stu-id="6e62d-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="6e62d-115">參數的`Print`方法， `aString`，建立方法，延伸<xref:System.String>類別。</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6e62d-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 <span data-ttu-id="6e62d-116">[!code-vb[VbVbalrExtensionMethods #&1;](./codesnippet/VisualBasic/extension-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-116">[!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="6e62d-117">請注意，擴充方法定義使用擴充屬性標記為`<Extension()>`。</span><span class="sxs-lookup"><span data-stu-id="6e62d-117">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="6e62d-118">標示方法定義的模組是選擇性的但必須標示為每個擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-118">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="6e62d-119"><xref:System.Runtime.CompilerServices>必須在匯入，才能存取此延伸模組屬性。</xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="6e62d-119"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="6e62d-120">擴充方法可以只在模組內宣告。</span><span class="sxs-lookup"><span data-stu-id="6e62d-120">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="6e62d-121">一般而言，擴充方法定義的模組不呼叫它的一個相同的模組。</span><span class="sxs-lookup"><span data-stu-id="6e62d-121">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="6e62d-122">相反地，包含擴充方法的模組匯入，如果需要才能將它帶入範圍。</span><span class="sxs-lookup"><span data-stu-id="6e62d-122">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="6e62d-123">包含的模組後`Print`是在範圍內，可以呼叫方法，就像是一般的執行個體方法，例如採用任何引數，好像`ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="6e62d-123">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 <span data-ttu-id="6e62d-124">[!code-vb[VbVbalrExtensionMethods #&2;](./codesnippet/VisualBasic/extension-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-124">[!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="6e62d-125">下一個範例中， `PrintAndPunctuate`，也是延伸<xref:System.String>，此時兩個參數定義。</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6e62d-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="6e62d-126">第一個參數， `aString`，會建立擴充方法，延伸<xref:System.String>.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6e62d-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="6e62d-127">第二個參數， `punc`，就是要標點符號的字串時，會傳遞做為引數呼叫該方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="6e62d-128">此方法會顯示後面的標點符號的字串。</span><span class="sxs-lookup"><span data-stu-id="6e62d-128">The method displays the string followed by the punctuation marks.</span></span>  
  
 <span data-ttu-id="6e62d-129">[!code-vb[VbVbalrExtensionMethods #&3;](./codesnippet/VisualBasic/extension-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-129">[!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="6e62d-130">方法由傳送中的字串引數呼叫`punc`:`example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="6e62d-130">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="6e62d-131">下列範例所示`Print`和`PrintAndPunctuate`定義和呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e62d-131">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="6e62d-132"><xref:System.Runtime.CompilerServices>匯入定義模組中若要啟用延伸模組屬性的存取權。</xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="6e62d-132"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6e62d-133">程式碼</span><span class="sxs-lookup"><span data-stu-id="6e62d-133">Code</span></span>  
  
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
  
 <span data-ttu-id="6e62d-134">接下來，擴充方法帶入範圍，而且呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e62d-134">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6e62d-135">註解</span><span class="sxs-lookup"><span data-stu-id="6e62d-135">Comments</span></span>  
 <span data-ttu-id="6e62d-136">所有必要時可以執行這些或類似的擴充方法是它們是在範圍內。</span><span class="sxs-lookup"><span data-stu-id="6e62d-136">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="6e62d-137">當在範圍內包含的擴充方法的模組，它會顯示在 IntelliSense 中，並可以如同一般的執行個體方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e62d-137">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="6e62d-138">請注意，方法會叫用時，未傳送引數第一個參數。</span><span class="sxs-lookup"><span data-stu-id="6e62d-138">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="6e62d-139">參數`aString`在前一個方法定義為繫結至`example`，執行個體`String`用來呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="6e62d-139">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="6e62d-140">編譯器會使用`example`當做引數傳送至第一個參數。</span><span class="sxs-lookup"><span data-stu-id="6e62d-140">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="6e62d-141">如果設定為物件呼叫擴充方法`Nothing`，擴充方法會執行。</span><span class="sxs-lookup"><span data-stu-id="6e62d-141">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="6e62d-142">這並不適用於一般的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-142">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="6e62d-143">您可以明確檢查是否有`Nothing`中擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-143">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="6e62d-144">可延伸的型別</span><span class="sxs-lookup"><span data-stu-id="6e62d-144">Types That Can Be Extended</span></span>  
 <span data-ttu-id="6e62d-145">您可以定義擴充方法的大部分型別可以用來表示 Visual Basic 的參數清單，包括下列︰</span><span class="sxs-lookup"><span data-stu-id="6e62d-145">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="6e62d-146">類別 （參考型別）</span><span class="sxs-lookup"><span data-stu-id="6e62d-146">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="6e62d-147">結構 （數值型別）</span><span class="sxs-lookup"><span data-stu-id="6e62d-147">Structures (value types)</span></span>  
  
-   <span data-ttu-id="6e62d-148">介面</span><span class="sxs-lookup"><span data-stu-id="6e62d-148">Interfaces</span></span>  
  
-   <span data-ttu-id="6e62d-149">委派</span><span class="sxs-lookup"><span data-stu-id="6e62d-149">Delegates</span></span>  
  
-   <span data-ttu-id="6e62d-150">ByRef 和 ByVal 引數</span><span class="sxs-lookup"><span data-stu-id="6e62d-150">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="6e62d-151">泛型方法的參數</span><span class="sxs-lookup"><span data-stu-id="6e62d-151">Generic method parameters</span></span>  
  
-   <span data-ttu-id="6e62d-152">陣列</span><span class="sxs-lookup"><span data-stu-id="6e62d-152">Arrays</span></span>  
  
 <span data-ttu-id="6e62d-153">第一個參數指定的擴充方法擴充的資料型別，因為它需要，而且不得為選擇性。</span><span class="sxs-lookup"><span data-stu-id="6e62d-153">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="6e62d-154">基於這個理由，`Optional`參數和`ParamArray`參數不可以是參數清單中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="6e62d-154">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="6e62d-155">擴充方法不會視為在晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="6e62d-155">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="6e62d-156">在下列範例中，陳述式`anObject.PrintMe()`引發<xref:System.MissingMemberException>例外狀況，如果您會看到相同的例外狀況，第二個`PrintMe`擴充方法定義已刪除。</xref:System.MissingMemberException></span><span class="sxs-lookup"><span data-stu-id="6e62d-156">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 <span data-ttu-id="6e62d-157">[!code-vb[VbVbalrExtensionMethods #&9;](./codesnippet/VisualBasic/extension-methods_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-157">[!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="6e62d-158">最佳作法</span><span class="sxs-lookup"><span data-stu-id="6e62d-158">Best Practices</span></span>  
 <span data-ttu-id="6e62d-159">擴充方法會提供方便且功能強大的方式來擴充現有的型別。</span><span class="sxs-lookup"><span data-stu-id="6e62d-159">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="6e62d-160">不過，若要順利使用這些方法，有一些要考慮的事項。</span><span class="sxs-lookup"><span data-stu-id="6e62d-160">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="6e62d-161">這些考量適用於主要是為了類別庫的作者，但可能會影響使用擴充方法的任何應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e62d-161">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="6e62d-162">一般來說，擴充方法，讓您將新增至不屬於您的型別會比您所控制的型別中加入的擴充方法更容易遭受攻擊。</span><span class="sxs-lookup"><span data-stu-id="6e62d-162">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="6e62d-163">有幾個可能會發生不屬於您可能會干擾您的擴充方法的類別。</span><span class="sxs-lookup"><span data-stu-id="6e62d-163">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="6e62d-164">如果已經不需要引數至參數的縮小轉換與呼叫的陳述式中的引數與相容的簽章存在任何可存取的執行個體成員，將任何擴充方法使用的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-164">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="6e62d-165">因此，如果在某個時間點的類別中加入適當的執行個體方法，您將依賴的現有擴充成員可能無法存取。</span><span class="sxs-lookup"><span data-stu-id="6e62d-165">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="6e62d-166">擴充方法的作者無法避免其他程式設計人員撰寫衝突可能高於原始副檔名的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-166">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="6e62d-167">您可以將放在自己的命名空間的擴充方法，以改善強固性。</span><span class="sxs-lookup"><span data-stu-id="6e62d-167">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="6e62d-168">您的程式庫的取用者可以包含命名空間或排除在外，或在命名空間，獨立於其餘的程式庫之中選取。</span><span class="sxs-lookup"><span data-stu-id="6e62d-168">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="6e62d-169">它可能比擴充類別，尤其是如果您並未擁有介面或類別擴充介面更安全。</span><span class="sxs-lookup"><span data-stu-id="6e62d-169">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="6e62d-170">在介面中的變更會影響實作它的每個類別。</span><span class="sxs-lookup"><span data-stu-id="6e62d-170">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="6e62d-171">因此，作者可能會比較不可能加入或變更介面中的方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-171">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="6e62d-172">不過，如果類別實作兩個具有相同簽章的擴充方法的介面，會顯示這兩種擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-172">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="6e62d-173">延伸您可以最特定的型別。</span><span class="sxs-lookup"><span data-stu-id="6e62d-173">Extend the most specific type you can.</span></span> <span data-ttu-id="6e62d-174">在階層中的型別，如果您選取要從中衍生許多其他類型，類型有執行個體方法或與您可能會妨礙其他延伸方法的各種層面。</span><span class="sxs-lookup"><span data-stu-id="6e62d-174">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="6e62d-175">擴充方法、 執行個體方法和屬性</span><span class="sxs-lookup"><span data-stu-id="6e62d-175">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="6e62d-176">當範圍內的執行個體方法具有與呼叫的陳述式的引數相容的簽章時，執行個體方法是選擇任何擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-176">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="6e62d-177">執行個體方法具有優先順序，即使此擴充方法是較佳的相符項目。</span><span class="sxs-lookup"><span data-stu-id="6e62d-177">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="6e62d-178">在下列範例中，`ExampleClass`包含名為執行個體方法`ExampleMethod`具有一個參數的型別`Integer`。</span><span class="sxs-lookup"><span data-stu-id="6e62d-178">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="6e62d-179">擴充方法`ExampleMethod`擴充`ExampleClass`，有一個參數的型別和`Long`。</span><span class="sxs-lookup"><span data-stu-id="6e62d-179">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 <span data-ttu-id="6e62d-180">[!code-vb[VbVbalrExtensionMethods #&4;](./codesnippet/VisualBasic/extension-methods_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-180">[!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]</span></span>  
  
 <span data-ttu-id="6e62d-181">第一次呼叫`ExampleMethod`下列程式碼會呼叫延伸方法，因為`arg1`是`Long`只能與相容和`Long`中擴充方法的參數。</span><span class="sxs-lookup"><span data-stu-id="6e62d-181">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="6e62d-182">第二次呼叫`ExampleMethod`有`Integer`引數， `arg2`，而且它會呼叫執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-182">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 <span data-ttu-id="6e62d-183">[!code-vb[VbVbalrExtensionMethods #&5;](./codesnippet/VisualBasic/extension-methods_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-183">[!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]</span></span>  
  
 <span data-ttu-id="6e62d-184">現在反向兩種方法中參數的資料型別︰</span><span class="sxs-lookup"><span data-stu-id="6e62d-184">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 <span data-ttu-id="6e62d-185">[!code-vb[VbVbalrExtensionMethods #&6;](./codesnippet/VisualBasic/extension-methods_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-185">[!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]</span></span>  
  
 <span data-ttu-id="6e62d-186">但這次中的程式碼`Main`呼叫的執行個體方法兩次。</span><span class="sxs-lookup"><span data-stu-id="6e62d-186">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="6e62d-187">這是因為兩者`arg1`和`arg2`具有擴展轉換`Long`，和執行個體方法優先於延伸方法，這兩種情況。</span><span class="sxs-lookup"><span data-stu-id="6e62d-187">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 <span data-ttu-id="6e62d-188">[!code-vb[VbVbalrExtensionMethods #&7;](./codesnippet/VisualBasic/extension-methods_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-188">[!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]</span></span>  
  
 <span data-ttu-id="6e62d-189">因此，擴充方法無法取代現有的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-189">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="6e62d-190">不過，當擴充方法有同名的執行個體方法，但是不會發生衝突之簽章，可存取這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-190">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="6e62d-191">例如，如果類別`ExampleClass`包含一個名為方法`ExampleMethod`採用任何引數，具有相同名稱的擴充方法，但允許不同的簽章，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6e62d-191">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 <span data-ttu-id="6e62d-192">[!code-vb[VbVbalrExtensionMethods #&8;](./codesnippet/VisualBasic/extension-methods_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e62d-192">[!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]</span></span>  
  
 <span data-ttu-id="6e62d-193">此程式碼的輸出如下所示︰</span><span class="sxs-lookup"><span data-stu-id="6e62d-193">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="6e62d-194">這種情況會更容易使用的屬性︰ 擴充方法的擴充方法具有相同的名稱做為其擴充的類別屬性，如果看不到，而且無法存取。</span><span class="sxs-lookup"><span data-stu-id="6e62d-194">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="6e62d-195">擴充方法優先順序</span><span class="sxs-lookup"><span data-stu-id="6e62d-195">Extension Method Precedence</span></span>  
 <span data-ttu-id="6e62d-196">兩個具有相同簽章的擴充方法是在範圍內且可存取，則具有較高的優先順序會叫用。</span><span class="sxs-lookup"><span data-stu-id="6e62d-196">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="6e62d-197">擴充方法的優先順序根據用來將方法帶入範圍的機制。</span><span class="sxs-lookup"><span data-stu-id="6e62d-197">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="6e62d-198">下列清單顯示優先順序階層架構中的，從最高到最低。</span><span class="sxs-lookup"><span data-stu-id="6e62d-198">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1.  <span data-ttu-id="6e62d-199">目前的模組內所定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-199">Extension methods defined inside the current module.</span></span>  
  
2.  <span data-ttu-id="6e62d-200">擴充方法定義內的資料類型在目前命名空間或任何一種其父代的優先順序高於父命名空間的子命名空間。</span><span class="sxs-lookup"><span data-stu-id="6e62d-200">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3.  <span data-ttu-id="6e62d-201">目前的檔案中的任何型別匯入定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-201">Extension methods defined inside any type imports in the current file.</span></span>  
  
4.  <span data-ttu-id="6e62d-202">目前的檔案中任何命名空間匯入定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-202">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5.  <span data-ttu-id="6e62d-203">任何專案層級類型匯入定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-203">Extension methods defined inside any project-level type imports.</span></span>  
  
6.  <span data-ttu-id="6e62d-204">任何專案層級命名空間匯入定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-204">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="6e62d-205">如果優先順序無法解決模稜兩可，您可以使用完整限定的名稱來指定您要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="6e62d-205">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="6e62d-206">如果`Print`前面範例中的方法定義於名為模組`StringExtensions`，完整的名稱是`StringExtensions.Print(example)`而不是`example.Print()`。</span><span class="sxs-lookup"><span data-stu-id="6e62d-206">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e62d-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e62d-207">See Also</span></span>  
 <span data-ttu-id="6e62d-208"><xref:System.Runtime.CompilerServices></xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="6e62d-208"><xref:System.Runtime.CompilerServices></span></span>   
 <span data-ttu-id="6e62d-209"><xref:System.Runtime.CompilerServices.ExtensionAttribute></xref:System.Runtime.CompilerServices.ExtensionAttribute></span><span class="sxs-lookup"><span data-stu-id="6e62d-209"><xref:System.Runtime.CompilerServices.ExtensionAttribute></span></span>   
<span data-ttu-id="6e62d-210"> [擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="6e62d-210"> [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span></span>  
<span data-ttu-id="6e62d-211"> [Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="6e62d-211"> [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="6e62d-212"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="6e62d-212"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="6e62d-213"> [選擇性參數](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="6e62d-213"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="6e62d-214"> [參數陣列](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="6e62d-214"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="6e62d-215"> [屬性概觀](../../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="6e62d-215"> [Attributes overview](../../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="6e62d-216"> [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span><span class="sxs-lookup"><span data-stu-id="6e62d-216"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span></span>
