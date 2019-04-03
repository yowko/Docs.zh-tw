---
title: HOW TO：撰寫擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d6f8b85945bd400d1f4b54a50260d72c750add8b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819101"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="179f5-102">HOW TO：撰寫擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="179f5-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="179f5-103">擴充方法可讓您將方法加入至現有的類別。</span><span class="sxs-lookup"><span data-stu-id="179f5-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="179f5-104">可以呼叫擴充方法，如同它是該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="179f5-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="179f5-105">若要定義擴充方法</span><span class="sxs-lookup"><span data-stu-id="179f5-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="179f5-106">Visual Studio 中開啟新的或現有的 Visual Basic 應用程式。</span><span class="sxs-lookup"><span data-stu-id="179f5-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="179f5-107">在您要在其中定義擴充方法的檔案頂端，加入下列 import 陳述式：</span><span class="sxs-lookup"><span data-stu-id="179f5-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="179f5-108">在新的或現有應用程式中的模組，開始以擴充屬性的方法定義：</span><span class="sxs-lookup"><span data-stu-id="179f5-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="179f5-109">不同之處在於第一個參數的型別必須是您想要擴充的資料類型，請以一般方式，宣告您的方法。</span><span class="sxs-lookup"><span data-stu-id="179f5-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="179f5-110">範例</span><span class="sxs-lookup"><span data-stu-id="179f5-110">Example</span></span>  
 <span data-ttu-id="179f5-111">下列範例會宣告模組中的擴充方法`StringExtensions`。</span><span class="sxs-lookup"><span data-stu-id="179f5-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="179f5-112">第二個模組中， `Module1`，匯入`StringExtensions`並呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="179f5-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="179f5-113">當呼叫它時，擴充方法必須在範圍內。</span><span class="sxs-lookup"><span data-stu-id="179f5-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="179f5-114">擴充方法`PrintAndPunctuate`擴充<xref:System.String>類別的方法，顯示的字串執行個體後面的標點符號中做為參數傳送的文字字串。</span><span class="sxs-lookup"><span data-stu-id="179f5-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
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
  
 <span data-ttu-id="179f5-115">請注意此方法時，定義具有兩個參數，而且呼叫只會與一個。</span><span class="sxs-lookup"><span data-stu-id="179f5-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="179f5-116">第一個參數， `aString`，在方法中定義繫結至`example`，執行個體`String`所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="179f5-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="179f5-117">此範例的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="179f5-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="179f5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="179f5-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="179f5-119">擴充方法</span><span class="sxs-lookup"><span data-stu-id="179f5-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="179f5-120">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="179f5-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="179f5-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="179f5-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="179f5-122">在 Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="179f5-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
