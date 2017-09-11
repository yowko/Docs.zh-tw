---
title: "變數的型別 &quot;&lt;variablename&gt;&quot; 將不會推斷，因為繫結至封閉範圍中的欄位 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
dev_langs:
- VB
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 0f954fda84c9fd1a4af5315be2329de117e6d169
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="d7e43-102">變數的型別 '&lt;variablename&gt;' 將不會推斷，因為繫結至封閉範圍中的欄位</span><span class="sxs-lookup"><span data-stu-id="d7e43-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="d7e43-103">變數的型別 '\<variablename >' 將不會推斷，因為繫結至封閉範圍中的欄位。</span><span class="sxs-lookup"><span data-stu-id="d7e43-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="d7e43-104">您可以變更名稱 '\<variablename >'，或使用完整限定的名稱 （例如 'Me.variablename' 或 'MyBase.variablename'）。</span><span class="sxs-lookup"><span data-stu-id="d7e43-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="d7e43-105">在程式碼中的迴圈控制變數具有相同名稱做為類別或其他封閉範圍的欄位。</span><span class="sxs-lookup"><span data-stu-id="d7e43-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="d7e43-106">因為使用控制變數，而沒有`As`子句，它會繫結至封閉範圍中的欄位和編譯器不會為其建立新的變數或推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="d7e43-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="d7e43-107">在下列範例中，`Index`中的控制項變數`For`陳述式中，繫結至`Index`欄位`Customer`類別。</span><span class="sxs-lookup"><span data-stu-id="d7e43-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="d7e43-108">編譯器不會建立新的變數，控制變數的`Index`或推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="d7e43-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="d7e43-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="d7e43-109">By default, this message is a warning.</span></span> <span data-ttu-id="d7e43-110">隱藏警告的方式或如何將警告視為錯誤的相關資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="d7e43-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d7e43-111">**錯誤識別碼︰** BC42110</span><span class="sxs-lookup"><span data-stu-id="d7e43-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="d7e43-112">解決這個警告</span><span class="sxs-lookup"><span data-stu-id="d7e43-112">To address this warning</span></span>  
  
-   <span data-ttu-id="d7e43-113">也不是類別的欄位名稱的識別項來變更其名稱，讓迴圈控制變數本機。</span><span class="sxs-lookup"><span data-stu-id="d7e43-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="d7e43-114">釐清的迴圈控制變數繫結至 [類別] 欄位加`Me.`變數名稱。</span><span class="sxs-lookup"><span data-stu-id="d7e43-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="d7e43-115">除了依賴區域型別推斷，使用`As`子句來指定迴圈控制變數的型別。</span><span class="sxs-lookup"><span data-stu-id="d7e43-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="d7e43-116">範例</span><span class="sxs-lookup"><span data-stu-id="d7e43-116">Example</span></span>  
 <span data-ttu-id="d7e43-117">下列程式碼會顯示就地使用第一個校正先前的範例。</span><span class="sxs-lookup"><span data-stu-id="d7e43-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7e43-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7e43-118">See Also</span></span>  
 <span data-ttu-id="d7e43-119">[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d7e43-119">[Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="d7e43-120"> [每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d7e43-120"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="d7e43-121"> [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d7e43-121"> [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="d7e43-122"> [如何︰ 參考物件的目前執行個體](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="d7e43-122"> [How to: Refer to the Current Instance of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span></span>  
<span data-ttu-id="d7e43-123"> [區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="d7e43-123"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="d7e43-124"> [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="d7e43-124"> [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>

