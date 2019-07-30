---
title: 作法：撰寫擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631030"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="068c3-102">作法：撰寫擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="068c3-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="068c3-103">擴充方法可讓您將方法加入至現有的類別。</span><span class="sxs-lookup"><span data-stu-id="068c3-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="068c3-104">您可以呼叫擴充方法, 就像它是該類別的實例一樣。</span><span class="sxs-lookup"><span data-stu-id="068c3-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="068c3-105">定義擴充方法</span><span class="sxs-lookup"><span data-stu-id="068c3-105">To define an extension method</span></span>

1. <span data-ttu-id="068c3-106">在 Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。</span><span class="sxs-lookup"><span data-stu-id="068c3-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="068c3-107">在您要定義擴充方法的檔案頂端, 加入下列 import 語句:</span><span class="sxs-lookup"><span data-stu-id="068c3-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="068c3-108">在新的或現有應用程式的模組內, 使用擴充屬性來開始方法定義:</span><span class="sxs-lookup"><span data-stu-id="068c3-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>

    ```vb
    <Extension()>
    ```

4. <span data-ttu-id="068c3-109">以一般方式宣告方法, 不同之處在于第一個參數的類型必須是您想要擴充的資料類型。</span><span class="sxs-lookup"><span data-stu-id="068c3-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="068c3-110">範例</span><span class="sxs-lookup"><span data-stu-id="068c3-110">Example</span></span>
 <span data-ttu-id="068c3-111">下列範例會在模組`StringExtensions`中宣告擴充方法。</span><span class="sxs-lookup"><span data-stu-id="068c3-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="068c3-112">第二個模組`Module1`, 則`StringExtensions`會匯入和呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="068c3-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="068c3-113">呼叫擴充方法時, 它必須在範圍內。</span><span class="sxs-lookup"><span data-stu-id="068c3-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="068c3-114">擴充方法`PrintAndPunctuate`會使用<xref:System.String>方法來擴充類別, 並在其中顯示字串實例, 後面接著以參數的形式傳送的標點符號符號字串。</span><span class="sxs-lookup"><span data-stu-id="068c3-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
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
  
 <span data-ttu-id="068c3-115">請注意, 方法是使用兩個參數所定義, 而且只會使用一個呼叫。</span><span class="sxs-lookup"><span data-stu-id="068c3-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="068c3-116">方法定義中的`aString`第一個參數會系結至`example`, `String`這是呼叫方法的實例。</span><span class="sxs-lookup"><span data-stu-id="068c3-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="068c3-117">此範例的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="068c3-117">The output of the example is as follows:</span></span>
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="068c3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="068c3-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="068c3-119">擴充方法</span><span class="sxs-lookup"><span data-stu-id="068c3-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="068c3-120">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="068c3-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="068c3-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="068c3-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="068c3-122">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="068c3-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
