---
title: 變數的型別&#39; &lt;variablename&gt; &#39;不會推斷，因為它繫結至封閉範圍中的欄位
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: cb423e8dcced6956eb86d484607915030c91412b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594279"
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="b0661-102">變數的型別&#39; &lt;variablename&gt; &#39;不會推斷，因為它繫結至封閉範圍中的欄位</span><span class="sxs-lookup"><span data-stu-id="b0661-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="b0661-103">變數的型別 '\<變數名稱 >' 不推斷，因為它繫結至封閉範圍中的欄位。</span><span class="sxs-lookup"><span data-stu-id="b0661-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="b0661-104">請變更名稱 '\<變數名稱 >'，或使用完整限定的名稱 （例如 'Me.variablename' 或 'MyBase.variablename'）。</span><span class="sxs-lookup"><span data-stu-id="b0661-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="b0661-105">在程式碼中的迴圈控制變數與其他封閉範圍或類別欄位具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0661-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="b0661-106">因為使用此控制項變數，而沒有`As`子句，它繫結至封閉範圍中中的欄位和編譯器不會為其建立新的變數或推斷其類型。</span><span class="sxs-lookup"><span data-stu-id="b0661-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="b0661-107">在下列範例中，`Index`中的控制變數`For`陳述式中，繫結至`Index`欄位`Customer`類別。</span><span class="sxs-lookup"><span data-stu-id="b0661-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="b0661-108">編譯器不會建立新的變數，控制變數`Index`或推斷其類型。</span><span class="sxs-lookup"><span data-stu-id="b0661-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
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
  
 <span data-ttu-id="b0661-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="b0661-109">By default, this message is a warning.</span></span> <span data-ttu-id="b0661-110">如需如何隱藏警告或將警告視為錯誤的資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="b0661-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b0661-111">**錯誤 ID:** BC42110</span><span class="sxs-lookup"><span data-stu-id="b0661-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="b0661-112">解決這個警告</span><span class="sxs-lookup"><span data-stu-id="b0661-112">To address this warning</span></span>  
  
-   <span data-ttu-id="b0661-113">也不是類別的欄位名稱的識別項來變更其名稱，使迴圈控制變數本機。</span><span class="sxs-lookup"><span data-stu-id="b0661-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="b0661-114">釐清，迴圈控制變數繫結至 [類別] 欄位加`Me.`變數名稱。</span><span class="sxs-lookup"><span data-stu-id="b0661-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="b0661-115">不要依賴區域類型推斷，而應使用`As`子句來指定 for 迴圈控制變數的類型。</span><span class="sxs-lookup"><span data-stu-id="b0661-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="b0661-116">範例</span><span class="sxs-lookup"><span data-stu-id="b0661-116">Example</span></span>  
 <span data-ttu-id="b0661-117">下列程式碼會顯示就地使用第一個校正先前的範例。</span><span class="sxs-lookup"><span data-stu-id="b0661-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0661-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0661-118">See Also</span></span>  
 [<span data-ttu-id="b0661-119">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="b0661-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="b0661-120">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="b0661-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="b0661-121">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="b0661-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="b0661-122">如何：參考物件目前的執行個體</span><span class="sxs-lookup"><span data-stu-id="b0661-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="b0661-123">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="b0661-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="b0661-124">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="b0661-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
