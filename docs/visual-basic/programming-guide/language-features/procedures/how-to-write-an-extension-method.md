---
title: HOW TO：撰寫擴充方法（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d01596d50db8ba1078e8ac82caa951418645c977
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004610"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="4bd6a-102">HOW TO：撰寫擴充方法（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4bd6a-102">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="4bd6a-103">擴充方法可讓您將方法加入至現有的類別。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="4bd6a-104">您可以呼叫擴充方法，就像它是該類別的實例一樣。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="4bd6a-105">定義擴充方法</span><span class="sxs-lookup"><span data-stu-id="4bd6a-105">To define an extension method</span></span>

1. <span data-ttu-id="4bd6a-106">在 Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="4bd6a-107">在您要定義擴充方法的檔案頂端，加入下列 import 語句：</span><span class="sxs-lookup"><span data-stu-id="4bd6a-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="4bd6a-108">在新的或現有應用程式的模組內，使用[`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute)屬性來開始方法定義：</span><span class="sxs-lookup"><span data-stu-id="4bd6a-108">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```
 
   <span data-ttu-id="4bd6a-109">請注意，`Extension` 屬性只能套用至 Visual Basic[模組](../../../language-reference/statements/module-statement.md)中的方法（@no__t 1 或 @no__t 2 程式）。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-109">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="4bd6a-110">如果您將它套用至 `Class` 或 `Structure` 的方法，Visual Basic 編譯器會產生錯誤[BC36551](../../../misc/bc36551.md)「擴充方法只能在模組中定義」。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-110">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="4bd6a-111">以一般方式宣告方法，不同之處在于第一個參數的類型必須是您想要擴充的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-111">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="4bd6a-112">範例</span><span class="sxs-lookup"><span data-stu-id="4bd6a-112">Example</span></span>

 <span data-ttu-id="4bd6a-113">下列範例會在模組 `StringExtensions` 中宣告擴充方法。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-113">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="4bd6a-114">第二個模組 `Module1`，會匯入 `StringExtensions`，並呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-114">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="4bd6a-115">呼叫擴充方法時，它必須在範圍內。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-115">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="4bd6a-116">擴充方法 `PrintAndPunctuate` 會使用方法來擴充 @no__t 1 類別，該方法會顯示字串實例，後面接著以參數的形式傳送的標點符號符號字串。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-116">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1
  
    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub
    
End Module
```
  
 <span data-ttu-id="4bd6a-117">請注意，方法是使用兩個參數所定義，而且只會使用一個呼叫。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-117">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="4bd6a-118">方法定義中的第一個參數（`aString`）系結至 `example`，也就是呼叫方法的 `String` 的實例。</span><span class="sxs-lookup"><span data-stu-id="4bd6a-118">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="4bd6a-119">此範例的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4bd6a-119">The output of the example is as follows:</span></span>
  
 ```console
 Hello?
 Hello!!!!
 ```
  
## <a name="see-also"></a><span data-ttu-id="4bd6a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bd6a-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="4bd6a-121">擴充方法</span><span class="sxs-lookup"><span data-stu-id="4bd6a-121">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="4bd6a-122">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="4bd6a-122">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="4bd6a-123">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="4bd6a-123">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="4bd6a-124">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="4bd6a-124">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
