---
title: "如何：撰寫擴充方法 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cdabf59886e7457a327ee9cde968a6a73f2280
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="443c2-102">如何：撰寫擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="443c2-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="443c2-103">擴充方法可讓您將方法加入至現有的類別。</span><span class="sxs-lookup"><span data-stu-id="443c2-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="443c2-104">可以呼叫擴充方法，就好像該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="443c2-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="443c2-105">若要定義的擴充方法</span><span class="sxs-lookup"><span data-stu-id="443c2-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="443c2-106">Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。</span><span class="sxs-lookup"><span data-stu-id="443c2-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="443c2-107">在您要定義的擴充方法的檔案頂端，加入下列 import 陳述式：</span><span class="sxs-lookup"><span data-stu-id="443c2-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="443c2-108">在新的或現有應用程式中的模組，開始使用擴充屬性和方法定義：</span><span class="sxs-lookup"><span data-stu-id="443c2-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="443c2-109">第一個參數的型別必須是您想要擴充的資料類型，請以一般方式，宣告您的方法。</span><span class="sxs-lookup"><span data-stu-id="443c2-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="443c2-110">範例</span><span class="sxs-lookup"><span data-stu-id="443c2-110">Example</span></span>  
 <span data-ttu-id="443c2-111">下列範例宣告模組中的擴充方法`StringExtensions`。</span><span class="sxs-lookup"><span data-stu-id="443c2-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="443c2-112">第二個模組， `Module1`，匯入`StringExtensions`呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="443c2-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="443c2-113">擴充方法必須在範圍內呼叫它。</span><span class="sxs-lookup"><span data-stu-id="443c2-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="443c2-114">擴充方法`PrintAndPunctuate`擴充<xref:System.String>類別顯示的字串執行個體的方法後面的標點符號中傳送做為參數的字串。</span><span class="sxs-lookup"><span data-stu-id="443c2-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
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
  
 <span data-ttu-id="443c2-115">請注意，方法是使用兩個參數定義只有一個呼叫。</span><span class="sxs-lookup"><span data-stu-id="443c2-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="443c2-116">第一個參數， `aString`，方法中定義為繫結至`example`，執行個體`String`用來呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="443c2-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="443c2-117">範例的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="443c2-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="443c2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="443c2-118">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="443c2-119">擴充方法</span><span class="sxs-lookup"><span data-stu-id="443c2-119">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="443c2-120">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="443c2-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="443c2-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="443c2-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="443c2-122">在 Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="443c2-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
