---
title: 不會推斷變數 '<variablename>' 的類型，因為它繫結至封閉範圍中的欄位
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: a595f38f6dd68b9c152bfa78ec0bebf36e173e17
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649972"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="3474a-102">變數的類型 '\<變數名稱 >' 將不會推斷，因為它繫結至封閉範圍中的欄位</span><span class="sxs-lookup"><span data-stu-id="3474a-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="3474a-103">變數的類型 '\<變數名稱 >' 將不會推斷，因為它繫結至封閉範圍中的欄位。</span><span class="sxs-lookup"><span data-stu-id="3474a-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="3474a-104">請變更名稱 '\<變數名稱 >'，或使用完整格式的名稱 （例如 'Me.variablename' 或 'MyBase.variablename'）。</span><span class="sxs-lookup"><span data-stu-id="3474a-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="3474a-105">在您的程式碼中的迴圈控制變數與類別或其他封入範圍的欄位具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="3474a-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="3474a-106">因為使用此控制項變數，而沒有`As`子句，它會繫結至封閉範圍中中的欄位和編譯器不會為它建立新的變數或推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="3474a-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="3474a-107">在下列範例中，`Index`中的控制變數`For`陳述式中，繫結至`Index`欄位中`Customer`類別。</span><span class="sxs-lookup"><span data-stu-id="3474a-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="3474a-108">編譯器不會建立新的變數，控制變數的`Index`或推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="3474a-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
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
  
 <span data-ttu-id="3474a-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="3474a-109">By default, this message is a warning.</span></span> <span data-ttu-id="3474a-110">如需如何隱藏警告或如何將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="3474a-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3474a-111">**錯誤 ID:** BC42110</span><span class="sxs-lookup"><span data-stu-id="3474a-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="3474a-112">解決這個警告</span><span class="sxs-lookup"><span data-stu-id="3474a-112">To address this warning</span></span>  
  
- <span data-ttu-id="3474a-113">也是不是類別的欄位名稱的識別項來變更其名稱，使迴圈控制變數本機。</span><span class="sxs-lookup"><span data-stu-id="3474a-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
- <span data-ttu-id="3474a-114">釐清，迴圈控制變數繫結至 [類別] 欄位前面加上`Me.`變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3474a-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
- <span data-ttu-id="3474a-115">而不是依賴區域型別推斷，使用`As`子句來指定迴圈控制變數的類型。</span><span class="sxs-lookup"><span data-stu-id="3474a-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="3474a-116">範例</span><span class="sxs-lookup"><span data-stu-id="3474a-116">Example</span></span>  
 <span data-ttu-id="3474a-117">下列程式碼就地顯示第一次為先前的範例。</span><span class="sxs-lookup"><span data-stu-id="3474a-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3474a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3474a-118">See also</span></span>

- [<span data-ttu-id="3474a-119">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="3474a-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="3474a-120">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="3474a-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="3474a-121">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="3474a-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3474a-122">如何：參考物件的目前執行個體</span><span class="sxs-lookup"><span data-stu-id="3474a-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="3474a-123">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="3474a-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="3474a-124">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="3474a-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
