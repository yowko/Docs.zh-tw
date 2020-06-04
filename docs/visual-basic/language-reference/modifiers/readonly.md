---
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 405297a25d4b948a6920bd989c7826e8b6f66bb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398203"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="f3804-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3804-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="f3804-103">指定可以讀取但不能寫入變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="f3804-103">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3804-104">備註</span><span class="sxs-lookup"><span data-stu-id="f3804-104">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="f3804-105">規則</span><span class="sxs-lookup"><span data-stu-id="f3804-105">Rules</span></span>

- <span data-ttu-id="f3804-106">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="f3804-106">**Declaration Context.**</span></span> <span data-ttu-id="f3804-107">您只能在模組層級使用 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="f3804-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="f3804-108">這表示元素的宣告內容 `ReadOnly` 必須是類別、結構或模組，而且不能是原始程式檔、命名空間或程式。</span><span class="sxs-lookup"><span data-stu-id="f3804-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="f3804-109">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="f3804-109">**Combined Modifiers.**</span></span> <span data-ttu-id="f3804-110">您不能 `ReadOnly` 在相同的宣告中同時指定與 `Static` 。</span><span class="sxs-lookup"><span data-stu-id="f3804-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="f3804-111">**指派值。**</span><span class="sxs-lookup"><span data-stu-id="f3804-111">**Assigning a Value.**</span></span> <span data-ttu-id="f3804-112">使用屬性的程式碼 `ReadOnly` 無法設定其值。</span><span class="sxs-lookup"><span data-stu-id="f3804-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="f3804-113">但可存取基礎儲存體的程式碼可以隨時指派或變更此值。</span><span class="sxs-lookup"><span data-stu-id="f3804-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="f3804-114">您只能 `ReadOnly` 在其宣告中，或在其定義所在之類別或結構的函式中，將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="f3804-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="f3804-115">使用 ReadOnly 變數的時機</span><span class="sxs-lookup"><span data-stu-id="f3804-115">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="f3804-116">在某些情況下，您無法使用[Const 語句](../statements/const-statement.md)來宣告和指派常數值。</span><span class="sxs-lookup"><span data-stu-id="f3804-116">There are situations in which you cannot use a [Const Statement](../statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="f3804-117">例如， `Const` 語句可能不會接受您想要指派的資料類型，或者您可能無法在編譯時期使用常數運算式來計算值。</span><span class="sxs-lookup"><span data-stu-id="f3804-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="f3804-118">您甚至可能不知道編譯時間的值。</span><span class="sxs-lookup"><span data-stu-id="f3804-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="f3804-119">在這些情況下，您可以使用 `ReadOnly` 變數來保存常數值。</span><span class="sxs-lookup"><span data-stu-id="f3804-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3804-120">如果變數的資料類型是參考型別（例如陣列或類別實例），即使變數本身為，也可以變更其成員 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="f3804-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="f3804-121">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f3804-121">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="f3804-122">當初始化時，由指向的陣列會 `characterArray()` 保留 "x"、"y" 和 "z"。</span><span class="sxs-lookup"><span data-stu-id="f3804-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="f3804-123">因為變數 `characterArray` 是 `ReadOnly` ，所以在初始化之後就無法變更它的值; 也就是說，您無法為它指派新的陣列。</span><span class="sxs-lookup"><span data-stu-id="f3804-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="f3804-124">不過，您可以變更一個或多個陣列成員的值。</span><span class="sxs-lookup"><span data-stu-id="f3804-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="f3804-125">在呼叫 `ChangeArrayElement` 程式之後，由指向的陣列會 `characterArray()` 保留 "x"、"M" 和 "z"。</span><span class="sxs-lookup"><span data-stu-id="f3804-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="f3804-126">請注意，這類似于將程式參數宣告為[ByVal](byval.md)，這可防止程式變更呼叫引數本身，但允許它變更其成員。</span><span class="sxs-lookup"><span data-stu-id="f3804-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="f3804-127">範例</span><span class="sxs-lookup"><span data-stu-id="f3804-127">Example</span></span>

<span data-ttu-id="f3804-128">下列範例會定義 `ReadOnly` 雇用員工之日期的屬性。</span><span class="sxs-lookup"><span data-stu-id="f3804-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="f3804-129">類別會在內部將屬性值儲存為 `Private` 變數，而且只有類別內的程式碼可以變更該值。</span><span class="sxs-lookup"><span data-stu-id="f3804-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="f3804-130">不過，屬性是 `Public` ，而可以存取類別的任何程式碼都可以讀取屬性。</span><span class="sxs-lookup"><span data-stu-id="f3804-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="f3804-131">`ReadOnly` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="f3804-131">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="f3804-132">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="f3804-132">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="f3804-133">Property Statement</span><span class="sxs-lookup"><span data-stu-id="f3804-133">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="f3804-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3804-134">See also</span></span>

- [<span data-ttu-id="f3804-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="f3804-135">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="f3804-136">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f3804-136">Keywords</span></span>](../keywords/index.md)
