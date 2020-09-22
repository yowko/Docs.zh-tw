---
title: 唯讀
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
ms.openlocfilehash: 3ca322da4e5f0edcbe12bf29bded863daabffe3d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867698"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="8fc3e-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fc3e-102">ReadOnly (Visual Basic)</span></span>

<span data-ttu-id="8fc3e-103">指定可以讀取但不寫入變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-103">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fc3e-104">備註</span><span class="sxs-lookup"><span data-stu-id="8fc3e-104">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="8fc3e-105">規則</span><span class="sxs-lookup"><span data-stu-id="8fc3e-105">Rules</span></span>

- <span data-ttu-id="8fc3e-106">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="8fc3e-106">**Declaration Context.**</span></span> <span data-ttu-id="8fc3e-107">您只能在模組層級使用 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="8fc3e-108">這表示元素的宣告內容 `ReadOnly` 必須是類別、結構或模組，且不能是原始程式檔、命名空間或程式。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="8fc3e-109">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="8fc3e-109">**Combined Modifiers.**</span></span> <span data-ttu-id="8fc3e-110">您無法 `ReadOnly` `Static` 在相同的宣告中同時指定。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="8fc3e-111">**指派值。**</span><span class="sxs-lookup"><span data-stu-id="8fc3e-111">**Assigning a Value.**</span></span> <span data-ttu-id="8fc3e-112">使用屬性的程式碼 `ReadOnly` 無法設定其值。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="8fc3e-113">但是可存取基礎儲存體的程式碼可隨時指派或變更該值。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="8fc3e-114">您只能將值指派給變數，或指派給其定義所在之類別或結構的函式中的 `ReadOnly` 變數。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="8fc3e-115">使用 ReadOnly 變數的時機</span><span class="sxs-lookup"><span data-stu-id="8fc3e-115">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="8fc3e-116">在某些情況下，您無法使用 [Const 語句](../statements/const-statement.md) 來宣告和指派常數值。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-116">There are situations in which you cannot use a [Const Statement](../statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="8fc3e-117">例如， `Const` 語句可能不接受您要指派的資料類型，或者您可能無法在編譯時期使用常數運算式來計算值。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="8fc3e-118">您甚至可能不知道編譯時間的值。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="8fc3e-119">在這些情況下，您可以使用 `ReadOnly` 變數來保存常數值。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8fc3e-120">如果變數的資料類型是參考型別（例如陣列或類別實例），即使變數本身為，也可以變更其成員 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="8fc3e-121">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-121">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="8fc3e-122">初始化時，會 `characterArray()` 保留 "x"、"y" 和 "z" 來指向的陣列。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="8fc3e-123">因為變數 `characterArray` 是 `ReadOnly` ，所以您無法在初始化之後變更它的值，也就是說，您無法指派新的陣列給它。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="8fc3e-124">不過，您可以變更一或多個陣列成員的值。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="8fc3e-125">在呼叫 `ChangeArrayElement` 程式之後，所指向的陣列會 `characterArray()` 保留 "x"、"M" 和 "z"。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="8fc3e-126">請注意，這類似于將程式參數宣告為 [ByVal](byval.md)，以防止程式變更呼叫引數本身，但允許它變更其成員。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="8fc3e-127">範例</span><span class="sxs-lookup"><span data-stu-id="8fc3e-127">Example</span></span>

<span data-ttu-id="8fc3e-128">下列範例會定義 `ReadOnly` 雇用員工的日期屬性。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="8fc3e-129">類別會在內部將屬性值儲存為 `Private` 變數，而只有類別內的程式碼可以變更該值。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="8fc3e-130">但是，屬性是 `Public` ，而且任何可以存取類別的程式碼都可以讀取屬性。</span><span class="sxs-lookup"><span data-stu-id="8fc3e-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="8fc3e-131">`ReadOnly` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="8fc3e-131">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="8fc3e-132">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="8fc3e-132">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="8fc3e-133">Property Statement</span><span class="sxs-lookup"><span data-stu-id="8fc3e-133">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="8fc3e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fc3e-134">See also</span></span>

- [<span data-ttu-id="8fc3e-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="8fc3e-135">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="8fc3e-136">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8fc3e-136">Keywords</span></span>](../keywords/index.md)
