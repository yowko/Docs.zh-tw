---
title: HOW TO：建立不會變更變數值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 626b46123e3047b391cd67d3e85c25c5432b2a69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640195"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="39afc-102">HOW TO：建立不會變更變數值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39afc-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="39afc-103">可能會互相矛盾，所以不會變更其值的變數概念。</span><span class="sxs-lookup"><span data-stu-id="39afc-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="39afc-104">但是常數不可行時，有很多情況下，而且最好有固定值的變數。</span><span class="sxs-lookup"><span data-stu-id="39afc-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="39afc-105">在這種情況中，您可以定義的成員變數[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="39afc-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="39afc-106">您無法使用[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)來宣告和指派常數值在下列情況：</span><span class="sxs-lookup"><span data-stu-id="39afc-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="39afc-107">`Const`陳述式不接受您想要使用的資料類型</span><span class="sxs-lookup"><span data-stu-id="39afc-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="39afc-108">您在編譯時期不知道值</span><span class="sxs-lookup"><span data-stu-id="39afc-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="39afc-109">無法在編譯時期計算的常數值</span><span class="sxs-lookup"><span data-stu-id="39afc-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="39afc-110">若要建立的變數，不會變更值</span><span class="sxs-lookup"><span data-stu-id="39afc-110">To create a variable that does not change in value</span></span>  
  
1.  <span data-ttu-id="39afc-111">在模組層級宣告的成員變數[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)，並包含[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="39afc-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="39afc-112">您可以指定`ReadOnly`只能在成員變數上。</span><span class="sxs-lookup"><span data-stu-id="39afc-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="39afc-113">這表示您必須定義在模組層級，任何程序之外的變數。</span><span class="sxs-lookup"><span data-stu-id="39afc-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2.  <span data-ttu-id="39afc-114">您可以計算在編譯時期的單一陳述式中的值，如果使用中的初始化子句`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="39afc-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="39afc-115">請遵循[作為](../../../../visual-basic/language-reference/statements/as-clause.md)子句以等號 (`=`)，後面接著一個運算式。</span><span class="sxs-lookup"><span data-stu-id="39afc-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="39afc-116">請確定編譯器可以評估此運算式為常數的值。</span><span class="sxs-lookup"><span data-stu-id="39afc-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="39afc-117">您可以指派值給`ReadOnly`變數一次。</span><span class="sxs-lookup"><span data-stu-id="39afc-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="39afc-118">一旦您這樣做時，任何程式碼，可以不變更其值。</span><span class="sxs-lookup"><span data-stu-id="39afc-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="39afc-119">如果您在編譯時期不知道值，或無法計算它在編譯時期，在單一陳述式中，您仍然可以指派其建構函式在執行階段。</span><span class="sxs-lookup"><span data-stu-id="39afc-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="39afc-120">若要這樣做，您必須宣告`ReadOnly`類別或結構的層級變數。</span><span class="sxs-lookup"><span data-stu-id="39afc-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="39afc-121">在該類別或結構的建構函式，計算變數的固定的值，並從建構函式傳回之前將它指派給變數。</span><span class="sxs-lookup"><span data-stu-id="39afc-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39afc-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39afc-122">See also</span></span>
- [<span data-ttu-id="39afc-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="39afc-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="39afc-124">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="39afc-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
