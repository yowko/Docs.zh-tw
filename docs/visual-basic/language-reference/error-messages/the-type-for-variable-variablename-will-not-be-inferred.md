---
title: 不會推斷變數 '<variablename>' 的類型，因為它繫結至封閉範圍中的欄位
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 98aeb5699fdd5e5e538a205acd37436019c3fc03
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363042"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="aef6f-102">不會推斷變數 '\<variablename>' 的類型，因為它繫結至封閉範圍中的欄位</span><span class="sxs-lookup"><span data-stu-id="aef6f-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="aef6f-103">\<variablename>將不會推斷變數 ' ' 的類型，因為它已系結至封閉範圍中的欄位。</span><span class="sxs-lookup"><span data-stu-id="aef6f-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="aef6f-104">請變更 ' ' 的名稱 \<variablename> ，或使用完整名稱（例如 ' variablename ' 或 ' MyBase. variablename '）。</span><span class="sxs-lookup"><span data-stu-id="aef6f-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="aef6f-105">程式碼中的迴圈控制變數與類別或其他封閉範圍的欄位名稱相同。</span><span class="sxs-lookup"><span data-stu-id="aef6f-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="aef6f-106">因為在沒有子句的情況下使用控制變數 `As` ，所以它會系結至封閉範圍中的欄位，而編譯器不會為它建立新的變數或推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="aef6f-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="aef6f-107">在下列範例中， `Index` 語句中的控制項變數會系結 `For` 至 `Index` 類別中的欄位 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="aef6f-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="aef6f-108">編譯器不會為控制項變數建立新的變數 `Index` 或推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="aef6f-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

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

<span data-ttu-id="aef6f-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="aef6f-109">By default, this message is a warning.</span></span> <span data-ttu-id="aef6f-110">如需如何隱藏警告或如何將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="aef6f-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="aef6f-111">**錯誤識別碼：** BC42110</span><span class="sxs-lookup"><span data-stu-id="aef6f-111">**Error ID:** BC42110</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="aef6f-112">解決這個警告</span><span class="sxs-lookup"><span data-stu-id="aef6f-112">To address this warning</span></span>

- <span data-ttu-id="aef6f-113">將迴圈控制變數的名稱變更為不是該類別的欄位名稱的識別碼，以將它設為區域變數。</span><span class="sxs-lookup"><span data-stu-id="aef6f-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="aef6f-114">澄清迴圈控制變數會藉由在變數名稱前面加上來系結至類別欄位 `Me.` 。</span><span class="sxs-lookup"><span data-stu-id="aef6f-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="aef6f-115">使用 `As` 子句來指定迴圈控制變數的類型，而不是依賴區欄位型別推斷。</span><span class="sxs-lookup"><span data-stu-id="aef6f-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="aef6f-116">範例</span><span class="sxs-lookup"><span data-stu-id="aef6f-116">Example</span></span>
 <span data-ttu-id="aef6f-117">下列程式碼顯示先前的範例，其中包含了第一個更正的位置。</span><span class="sxs-lookup"><span data-stu-id="aef6f-117">The following code shows the earlier example with the first correction in place.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aef6f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aef6f-118">See also</span></span>

- [<span data-ttu-id="aef6f-119">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="aef6f-119">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="aef6f-120">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="aef6f-120">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="aef6f-121">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="aef6f-121">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="aef6f-122">如何：參考物件目前的執行個體</span><span class="sxs-lookup"><span data-stu-id="aef6f-122">How to: Refer to the Current Instance of an Object</span></span>](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="aef6f-123">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="aef6f-123">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="aef6f-124">Me、My、MyBase 及 MyClass</span><span class="sxs-lookup"><span data-stu-id="aef6f-124">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
