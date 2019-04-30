---
title: ReadOnly (Visual Basic)
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
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051854"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="f6d79-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6d79-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="f6d79-103">指定的變數或屬性可讀取但不是會寫入。</span><span class="sxs-lookup"><span data-stu-id="f6d79-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6d79-104">備註</span><span class="sxs-lookup"><span data-stu-id="f6d79-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f6d79-105">規則</span><span class="sxs-lookup"><span data-stu-id="f6d79-105">Rules</span></span>  
  
- <span data-ttu-id="f6d79-106">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="f6d79-106">**Declaration Context.**</span></span> <span data-ttu-id="f6d79-107">您只能在模組層級使用 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="f6d79-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="f6d79-108">這表示的宣告內容`ReadOnly`項目必須是類別、 結構或模組，並不能是原始程式檔、 命名空間或程序。</span><span class="sxs-lookup"><span data-stu-id="f6d79-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="f6d79-109">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="f6d79-109">**Combined Modifiers.**</span></span> <span data-ttu-id="f6d79-110">您無法指定`ReadOnly`搭配`Static`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="f6d79-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
- <span data-ttu-id="f6d79-111">**指派的值。**</span><span class="sxs-lookup"><span data-stu-id="f6d79-111">**Assigning a Value.**</span></span> <span data-ttu-id="f6d79-112">程式碼使用`ReadOnly`屬性無法設定其值。</span><span class="sxs-lookup"><span data-stu-id="f6d79-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="f6d79-113">但是，具有存取權的基礎儲存體的程式碼可以指派，或隨時變更此值。</span><span class="sxs-lookup"><span data-stu-id="f6d79-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="f6d79-114">您可以指派值給`ReadOnly`變數只在其宣告或類別或結構中定義的建構函式中。</span><span class="sxs-lookup"><span data-stu-id="f6d79-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="f6d79-115">何時使用唯讀變數</span><span class="sxs-lookup"><span data-stu-id="f6d79-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="f6d79-116">您無法使用的情況下[Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)來宣告和指派常數值。</span><span class="sxs-lookup"><span data-stu-id="f6d79-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="f6d79-117">比方說，`Const`陳述式可能不會接受您想要指派，資料類型，或您可能無法在編譯時期常數的運算式與計算的值。</span><span class="sxs-lookup"><span data-stu-id="f6d79-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="f6d79-118">然後，您甚至可能不知道值在編譯時期。</span><span class="sxs-lookup"><span data-stu-id="f6d79-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="f6d79-119">在這些情況下，您可以使用`ReadOnly`儲存常數值的變數。</span><span class="sxs-lookup"><span data-stu-id="f6d79-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f6d79-120">即使變數本身是，如果變數的資料型別是參考類型，例如陣列或類別執行個體，可以變更其成員`ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="f6d79-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="f6d79-121">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f6d79-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="f6d79-122">當初始化時，陣列指向`characterArray()`保留"x"，"y"，"z"。</span><span class="sxs-lookup"><span data-stu-id="f6d79-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="f6d79-123">因為變數`characterArray`是`ReadOnly`一旦初始化; 也就是說，您無法變更其值，您無法將新的陣列指派給它。</span><span class="sxs-lookup"><span data-stu-id="f6d79-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="f6d79-124">不過，您可以變更一個或多個陣列成員的值。</span><span class="sxs-lookup"><span data-stu-id="f6d79-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="f6d79-125">下列程序呼叫`changeArrayElement`，所指陣列`characterArray()`保留"x"，"M"、"z"。</span><span class="sxs-lookup"><span data-stu-id="f6d79-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="f6d79-126">請注意，這類似於宣告的程序參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)，防止程序呼叫中引數本身的變更，但是可讓它來變更其成員。</span><span class="sxs-lookup"><span data-stu-id="f6d79-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6d79-127">範例</span><span class="sxs-lookup"><span data-stu-id="f6d79-127">Example</span></span>  
 <span data-ttu-id="f6d79-128">下列範例會定義`ReadOnly`雇用員工的日期屬性。</span><span class="sxs-lookup"><span data-stu-id="f6d79-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="f6d79-129">屬性的值在內部類別會儲存`Private`變數，並只在類別內的程式碼可以變更該值。</span><span class="sxs-lookup"><span data-stu-id="f6d79-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="f6d79-130">不過，屬性是`Public`，並可存取該類別的任何程式碼可以讀取屬性。</span><span class="sxs-lookup"><span data-stu-id="f6d79-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="f6d79-131">`ReadOnly` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="f6d79-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f6d79-132">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="f6d79-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="f6d79-133">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="f6d79-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f6d79-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6d79-134">See also</span></span>

- [<span data-ttu-id="f6d79-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="f6d79-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="f6d79-136">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f6d79-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
