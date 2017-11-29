---
title: "如何：呼叫擴充方法 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25b5a86af15694e6f64f96a5d5d645a01f8f1f12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="c9747-102">如何：呼叫擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9747-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="c9747-103">擴充方法可讓您將方法加入至現有的類別。</span><span class="sxs-lookup"><span data-stu-id="c9747-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="c9747-104">擴充方法宣告，然後帶入範圍之後，您可以像擴充類型的執行個體方法呼叫它。</span><span class="sxs-lookup"><span data-stu-id="c9747-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="c9747-105">如需如何撰寫擴充方法的詳細資訊，請參閱[How to： 撰寫擴充方法](./how-to-write-an-extension-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c9747-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="c9747-106">擴充方法，請參閱下列指示`PrintAndPunctuate`，這會顯示叫用它，後面接著任何值的字串執行個體中的第二個參數，傳送`punc`。</span><span class="sxs-lookup"><span data-stu-id="c9747-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
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
  
 <span data-ttu-id="c9747-107">呼叫時，此方法必須在範圍內。</span><span class="sxs-lookup"><span data-stu-id="c9747-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="c9747-108">呼叫擴充方法</span><span class="sxs-lookup"><span data-stu-id="c9747-108">To call an extension method</span></span>  
  
1.  <span data-ttu-id="c9747-109">宣告具有擴充方法的第一個參數的資料類型的變數。</span><span class="sxs-lookup"><span data-stu-id="c9747-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="c9747-110">如`PrintAndPunctuate`，您需要<xref:System.String>變數：</span><span class="sxs-lookup"><span data-stu-id="c9747-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  <span data-ttu-id="c9747-111">變數將會叫用擴充方法，和其值會繫結至第一個參數， `aString`。</span><span class="sxs-lookup"><span data-stu-id="c9747-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="c9747-112">下列呼叫的陳述式將會顯示`Ready?`。</span><span class="sxs-lookup"><span data-stu-id="c9747-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="c9747-113">請注意，這個擴充方法的呼叫看起來就像呼叫任何一個<xref:System.String>執行個體需要一個參數的方法：</span><span class="sxs-lookup"><span data-stu-id="c9747-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  <span data-ttu-id="c9747-114">宣告另一個字串變數，並呼叫方法，一次，以查看其運作以任何字串。</span><span class="sxs-lookup"><span data-stu-id="c9747-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="c9747-115">結果現在是： `or not!!!`。</span><span class="sxs-lookup"><span data-stu-id="c9747-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9747-116">範例</span><span class="sxs-lookup"><span data-stu-id="c9747-116">Example</span></span>  
 <span data-ttu-id="c9747-117">下列程式碼是完整的範例，在建立和使用簡單的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="c9747-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9747-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9747-118">See Also</span></span>  
 [<span data-ttu-id="c9747-119">如何：撰寫擴充方法</span><span class="sxs-lookup"><span data-stu-id="c9747-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)  
 [<span data-ttu-id="c9747-120">擴充方法</span><span class="sxs-lookup"><span data-stu-id="c9747-120">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="c9747-121">在 Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="c9747-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
