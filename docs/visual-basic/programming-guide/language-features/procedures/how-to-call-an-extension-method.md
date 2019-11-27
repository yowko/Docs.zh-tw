---
title: 如何：呼叫擴充方法
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: a19705a8f90833d48869df26a18d19b0ad1488e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340400"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="21f0c-102">如何：呼叫擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21f0c-102">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="21f0c-103">擴充方法可讓您將方法加入至現有的類別。</span><span class="sxs-lookup"><span data-stu-id="21f0c-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="21f0c-104">在宣告擴充方法並將其納入範圍之後，您就可以像它所擴充之類型的實例方法一樣呼叫它。</span><span class="sxs-lookup"><span data-stu-id="21f0c-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="21f0c-105">如需如何撰寫擴充方法的詳細資訊，請參閱[如何：撰寫擴充方法](./how-to-write-an-extension-method.md)。</span><span class="sxs-lookup"><span data-stu-id="21f0c-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="21f0c-106">下列指示會參考擴充方法 `PrintAndPunctuate`，它會顯示叫用它的字串實例，後面接著針對第二個參數所傳送的任何值，`punc`。</span><span class="sxs-lookup"><span data-stu-id="21f0c-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

<span data-ttu-id="21f0c-107">方法在呼叫時必須在範圍內。</span><span class="sxs-lookup"><span data-stu-id="21f0c-107">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="21f0c-108">呼叫擴充方法</span><span class="sxs-lookup"><span data-stu-id="21f0c-108">To call an extension method</span></span>

1. <span data-ttu-id="21f0c-109">宣告具有擴充方法第一個參數之資料類型的變數。</span><span class="sxs-lookup"><span data-stu-id="21f0c-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="21f0c-110">針對 `PrintAndPunctuate`，您需要 <xref:System.String> 變數：</span><span class="sxs-lookup"><span data-stu-id="21f0c-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="21f0c-111">該變數會叫用擴充方法，而且其值會系結至第一個參數 `aString`。</span><span class="sxs-lookup"><span data-stu-id="21f0c-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="21f0c-112">下列呼叫語句會顯示 `Ready?`。</span><span class="sxs-lookup"><span data-stu-id="21f0c-112">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="21f0c-113">請注意，此擴充方法的呼叫看起來就像是呼叫任何一個需要一個參數的 <xref:System.String> 實例方法：</span><span class="sxs-lookup"><span data-stu-id="21f0c-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="21f0c-114">請宣告另一個字串變數，然後再次呼叫方法，以查看它是否能與任何字串搭配使用。</span><span class="sxs-lookup"><span data-stu-id="21f0c-114">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="21f0c-115">這次的結果是： `or not!!!`。</span><span class="sxs-lookup"><span data-stu-id="21f0c-115">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="21f0c-116">範例</span><span class="sxs-lookup"><span data-stu-id="21f0c-116">Example</span></span>
 <span data-ttu-id="21f0c-117">下列程式碼是建立和使用簡單擴充方法的完整範例。</span><span class="sxs-lookup"><span data-stu-id="21f0c-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a><span data-ttu-id="21f0c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21f0c-118">See also</span></span>

- [<span data-ttu-id="21f0c-119">如何：撰寫擴充方法</span><span class="sxs-lookup"><span data-stu-id="21f0c-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="21f0c-120">擴充方法</span><span class="sxs-lookup"><span data-stu-id="21f0c-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="21f0c-121">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="21f0c-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
