---
title: 作法：建立不會在值中變更的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d201e95463dd0431825fee03ebfd340ac80cc552
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630893"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="07d93-102">HOW TO：建立不會在值中變更的變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07d93-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="07d93-103">未變更其值的變數概念可能會顯示為衝突。</span><span class="sxs-lookup"><span data-stu-id="07d93-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="07d93-104">但在某些情況下, 常數並不可行, 而且具有固定值的變數會很有用。</span><span class="sxs-lookup"><span data-stu-id="07d93-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="07d93-105">在這種情況下, 您可以使用[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字來定義成員變數。</span><span class="sxs-lookup"><span data-stu-id="07d93-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="07d93-106">在下列情況下, 您無法使用[Const 語句](../../../../visual-basic/language-reference/statements/const-statement.md)來宣告和指派常數值:</span><span class="sxs-lookup"><span data-stu-id="07d93-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="07d93-107">`Const`語句不接受您想要使用的資料類型</span><span class="sxs-lookup"><span data-stu-id="07d93-107">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="07d93-108">您在編譯時期不知道此值</span><span class="sxs-lookup"><span data-stu-id="07d93-108">You do not know the value at compile time</span></span>

- <span data-ttu-id="07d93-109">您無法在編譯時期計算常數值</span><span class="sxs-lookup"><span data-stu-id="07d93-109">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="07d93-110">若要建立不會在值中變更的變數</span><span class="sxs-lookup"><span data-stu-id="07d93-110">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="07d93-111">在模組層級, 使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告成員變數, 並包含[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="07d93-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="07d93-112">您只能在`ReadOnly`成員變數上指定。</span><span class="sxs-lookup"><span data-stu-id="07d93-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="07d93-113">這表示您必須在任何程式之外的模組層級定義變數。</span><span class="sxs-lookup"><span data-stu-id="07d93-113">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="07d93-114">如果您可以在編譯時期計算單一語句中的值, 請在`Dim`語句中使用初始化子句。</span><span class="sxs-lookup"><span data-stu-id="07d93-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="07d93-115">請在[As](../../../../visual-basic/language-reference/statements/as-clause.md)子句後面加上等號`=`(), 後面接著運算式。</span><span class="sxs-lookup"><span data-stu-id="07d93-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="07d93-116">請確定編譯器可以將此運算式評估為常數值。</span><span class="sxs-lookup"><span data-stu-id="07d93-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="07d93-117">您只能將值指派給`ReadOnly`變數一次。</span><span class="sxs-lookup"><span data-stu-id="07d93-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="07d93-118">一旦您這麼做, 任何程式碼都不會變更其值。</span><span class="sxs-lookup"><span data-stu-id="07d93-118">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="07d93-119">如果您在編譯時期不知道此值, 或是在編譯時期無法使用單一語句來計算該值, 您仍然可以在執行時間于函式中指派它。</span><span class="sxs-lookup"><span data-stu-id="07d93-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="07d93-120">若要這樣做, 您必須`ReadOnly`在類別或結構層級宣告變數。</span><span class="sxs-lookup"><span data-stu-id="07d93-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="07d93-121">在該類別或結構的函式中, 計算變數的固定值, 並將它指派給變數, 然後再從函式傳回。</span><span class="sxs-lookup"><span data-stu-id="07d93-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="07d93-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07d93-122">See also</span></span>

- [<span data-ttu-id="07d93-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="07d93-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="07d93-124">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="07d93-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
