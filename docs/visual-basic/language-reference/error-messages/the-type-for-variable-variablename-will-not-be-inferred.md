---
title: 不會推斷變數 '<variablename>' 的類型，因為它繫結至封閉範圍中的欄位
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 1ad7b9d0a610842dd6c50ee198f5bb5fa3eb68cf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870478"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="00007-102">不會推斷變數 '\<variablename>' 的類型，因為它繫結至封閉範圍中的欄位</span><span class="sxs-lookup"><span data-stu-id="00007-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="00007-103">\<variablename>將不會推斷變數 ' ' 的類型，因為它已系結至封閉範圍內的欄位。</span><span class="sxs-lookup"><span data-stu-id="00007-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="00007-104">請變更 ' ' 的名稱 \<variablename> ，或使用完整名稱 (例如 ' variablename ' 或 ' MyBase. variablename ' ) 。</span><span class="sxs-lookup"><span data-stu-id="00007-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="00007-105">您程式碼中的迴圈控制變數與類別或其他封閉範圍的欄位有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="00007-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="00007-106">因為在沒有子句的情況下使用控制項變數 `As` ，所以它會系結至封閉範圍內的欄位，而編譯器不會為它建立新的變數或推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="00007-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="00007-107">在下列範例中， `Index` 語句中的控制項變數系結 `For` 至 `Index` 類別中的欄位 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="00007-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="00007-108">編譯器不會為控制項變數建立新的變數 `Index` 或推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="00007-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

```vb
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

<span data-ttu-id="00007-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="00007-109">By default, this message is a warning.</span></span> <span data-ttu-id="00007-110">如需如何隱藏警告或如何將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="00007-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="00007-111">**錯誤識別碼：** BC42110</span><span class="sxs-lookup"><span data-stu-id="00007-111">**Error ID:** BC42110</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="00007-112">解決這個警告</span><span class="sxs-lookup"><span data-stu-id="00007-112">To address this warning</span></span>

- <span data-ttu-id="00007-113">將迴圈控制變數的名稱變更為不是類別之功能變數名稱的識別碼，以使其變成本機。</span><span class="sxs-lookup"><span data-stu-id="00007-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="00007-114">請注意，迴圈控制變數會藉由在變數名稱前面加上系結至類別欄位 `Me.` 。</span><span class="sxs-lookup"><span data-stu-id="00007-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="00007-115">您 `As` 可以使用子句來指定迴圈控制變數的類型，而不需要依賴區欄位型別推斷。</span><span class="sxs-lookup"><span data-stu-id="00007-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="00007-116">範例</span><span class="sxs-lookup"><span data-stu-id="00007-116">Example</span></span>

 <span data-ttu-id="00007-117">下列程式碼顯示先前的範例，其中的第一個更正已備妥。</span><span class="sxs-lookup"><span data-stu-id="00007-117">The following code shows the earlier example with the first correction in place.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="00007-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00007-118">See also</span></span>

- [<span data-ttu-id="00007-119">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="00007-119">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="00007-120">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="00007-120">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="00007-121">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="00007-121">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="00007-122">如何：參考物件目前的執行個體</span><span class="sxs-lookup"><span data-stu-id="00007-122">How to: Refer to the Current Instance of an Object</span></span>](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="00007-123">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="00007-123">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="00007-124">Me、My、MyBase 及 MyClass</span><span class="sxs-lookup"><span data-stu-id="00007-124">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
