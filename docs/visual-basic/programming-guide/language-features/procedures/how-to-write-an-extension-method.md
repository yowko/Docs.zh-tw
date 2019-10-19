---
title: 如何：撰寫擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 4671728330614f0f3da23fd90f5e635ddcf46578
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581149"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="f9268-102">如何：撰寫擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9268-102">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="f9268-103">擴充方法可讓您將方法加入至現有的類別。</span><span class="sxs-lookup"><span data-stu-id="f9268-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="f9268-104">您可以呼叫擴充方法，就像它是該類別的實例一樣。</span><span class="sxs-lookup"><span data-stu-id="f9268-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="f9268-105">定義擴充方法</span><span class="sxs-lookup"><span data-stu-id="f9268-105">To define an extension method</span></span>

1. <span data-ttu-id="f9268-106">在 Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9268-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="f9268-107">在您要定義擴充方法的檔案頂端，加入下列 import 語句：</span><span class="sxs-lookup"><span data-stu-id="f9268-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="f9268-108">在新的或現有應用程式的模組內，使用[`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute)屬性來開始方法定義：</span><span class="sxs-lookup"><span data-stu-id="f9268-108">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```

    <span data-ttu-id="f9268-109">請注意，`Extension` 屬性只能套用至 Visual Basic[模組](../../../language-reference/statements/module-statement.md)中的方法（`Sub` 或 `Function` 程式）。</span><span class="sxs-lookup"><span data-stu-id="f9268-109">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="f9268-110">如果您將它套用至 `Class` 或 `Structure` 中的方法，Visual Basic 編譯器會產生錯誤[BC36551](../../../misc/bc36551.md)「擴充方法只能在模組中定義」。</span><span class="sxs-lookup"><span data-stu-id="f9268-110">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="f9268-111">以一般方式宣告方法，不同之處在于第一個參數的類型必須是您想要擴充的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f9268-111">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="f9268-112">範例</span><span class="sxs-lookup"><span data-stu-id="f9268-112">Example</span></span>

<span data-ttu-id="f9268-113">下列範例會在模組 `StringExtensions` 中宣告擴充方法。</span><span class="sxs-lookup"><span data-stu-id="f9268-113">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="f9268-114">第二個模組 `Module1`，會匯入 `StringExtensions` 並呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="f9268-114">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="f9268-115">呼叫擴充方法時，它必須在範圍內。</span><span class="sxs-lookup"><span data-stu-id="f9268-115">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="f9268-116">擴充方法 `PrintAndPunctuate` 使用方法來擴充 <xref:System.String> 類別，並在其中顯示字串實例，後面接著以參數的形式傳送之標點符號符號的字串。</span><span class="sxs-lookup"><span data-stu-id="f9268-116">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>

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

<span data-ttu-id="f9268-117">請注意，方法是使用兩個參數所定義，而且只會使用一個呼叫。</span><span class="sxs-lookup"><span data-stu-id="f9268-117">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="f9268-118">方法定義中的第一個參數（`aString`）會系結至 `example`，這是呼叫方法的 `String` 實例。</span><span class="sxs-lookup"><span data-stu-id="f9268-118">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="f9268-119">此範例的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="f9268-119">The output of the example is as follows:</span></span>

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a><span data-ttu-id="f9268-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9268-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="f9268-121">擴充方法</span><span class="sxs-lookup"><span data-stu-id="f9268-121">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="f9268-122">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="f9268-122">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="f9268-123">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="f9268-123">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f9268-124">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="f9268-124">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
