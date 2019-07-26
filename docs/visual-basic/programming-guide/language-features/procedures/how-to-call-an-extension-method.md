---
title: 作法：呼叫擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512665"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="d2201-102">作法：呼叫擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2201-102">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="d2201-103">擴充方法可讓您將方法加入至現有的類別。</span><span class="sxs-lookup"><span data-stu-id="d2201-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="d2201-104">在宣告擴充方法並將其納入範圍之後, 您就可以像它所擴充之類型的實例方法一樣呼叫它。</span><span class="sxs-lookup"><span data-stu-id="d2201-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="d2201-105">如需如何撰寫擴充方法的詳細資訊, 請參閱[如何:撰寫擴充方法](./how-to-write-an-extension-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d2201-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="d2201-106">下列指示會參考擴充方法`PrintAndPunctuate`, 它會顯示叫用它的字串實例, 後面接著針對第二個`punc`參數傳送的任何值。</span><span class="sxs-lookup"><span data-stu-id="d2201-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

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

<span data-ttu-id="d2201-107">方法在呼叫時必須在範圍內。</span><span class="sxs-lookup"><span data-stu-id="d2201-107">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="d2201-108">呼叫擴充方法</span><span class="sxs-lookup"><span data-stu-id="d2201-108">To call an extension method</span></span>

1. <span data-ttu-id="d2201-109">宣告具有擴充方法第一個參數之資料類型的變數。</span><span class="sxs-lookup"><span data-stu-id="d2201-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="d2201-110">針對`PrintAndPunctuate`, 您需要一個<xref:System.String>變數:</span><span class="sxs-lookup"><span data-stu-id="d2201-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="d2201-111">該變數會叫用擴充方法, 而且其值會系結至第一個參數`aString`。</span><span class="sxs-lookup"><span data-stu-id="d2201-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="d2201-112">將會顯示`Ready?`下列呼叫語句。</span><span class="sxs-lookup"><span data-stu-id="d2201-112">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="d2201-113">請注意, 此擴充方法的呼叫看起來就像是呼叫任何一個<xref:System.String>需要一個參數的實例方法一樣:</span><span class="sxs-lookup"><span data-stu-id="d2201-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="d2201-114">請宣告另一個字串變數, 然後再次呼叫方法, 以查看它是否能與任何字串搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d2201-114">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="d2201-115">這次的結果是: `or not!!!`。</span><span class="sxs-lookup"><span data-stu-id="d2201-115">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="d2201-116">範例</span><span class="sxs-lookup"><span data-stu-id="d2201-116">Example</span></span>
 <span data-ttu-id="d2201-117">下列程式碼是建立和使用簡單擴充方法的完整範例。</span><span class="sxs-lookup"><span data-stu-id="d2201-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d2201-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2201-118">See also</span></span>

- [<span data-ttu-id="d2201-119">如何：撰寫擴充方法</span><span class="sxs-lookup"><span data-stu-id="d2201-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="d2201-120">擴充方法</span><span class="sxs-lookup"><span data-stu-id="d2201-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="d2201-121">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="d2201-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
