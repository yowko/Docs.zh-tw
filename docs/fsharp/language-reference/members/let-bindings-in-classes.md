---
title: 類別中的 let 繫結
description: 瞭解如何使用類別定義中的「let」 F#系結，定義類別的私用欄位和私用函式。
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216525"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="504aa-103">類別中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="504aa-103">let Bindings in Classes</span></span>

<span data-ttu-id="504aa-104">您可以使用`let`類別定義中的系結F# ，定義類別的私用欄位和私用函式。</span><span class="sxs-lookup"><span data-stu-id="504aa-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="504aa-105">語法</span><span class="sxs-lookup"><span data-stu-id="504aa-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="504aa-106">備註</span><span class="sxs-lookup"><span data-stu-id="504aa-106">Remarks</span></span>

<span data-ttu-id="504aa-107">先前的語法會出現在類別標題和繼承宣告之後，但在任何成員定義之前。</span><span class="sxs-lookup"><span data-stu-id="504aa-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="504aa-108">語法類似于`let`類別外的系結，但是在類別中定義的名稱具有限制為類別的範圍。</span><span class="sxs-lookup"><span data-stu-id="504aa-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="504aa-109">`let`系結會建立私用欄位或函式; 若要公開資料或函數，請宣告屬性或成員方法。</span><span class="sxs-lookup"><span data-stu-id="504aa-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="504aa-110">不是靜態的系結稱為「實例系`let`結」（instance binding）。 `let`</span><span class="sxs-lookup"><span data-stu-id="504aa-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="504aa-111">建立`let`物件時，會執行實例系結。</span><span class="sxs-lookup"><span data-stu-id="504aa-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="504aa-112">靜態`let`系結是類別之靜態初始化運算式的一部分，保證會在第一次使用型別之前執行。</span><span class="sxs-lookup"><span data-stu-id="504aa-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="504aa-113">實例`let`系結中的程式碼可以使用主要的函式的參數。</span><span class="sxs-lookup"><span data-stu-id="504aa-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="504aa-114">類別中的系結不允許`let`屬性和存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="504aa-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="504aa-115">下列程式碼範例說明類別中的`let`數種系結類型。</span><span class="sxs-lookup"><span data-stu-id="504aa-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="504aa-116">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="504aa-116">The output is as follows.</span></span>

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="504aa-117">建立欄位的替代方式</span><span class="sxs-lookup"><span data-stu-id="504aa-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="504aa-118">您也可以使用`val`關鍵字來建立私用欄位。</span><span class="sxs-lookup"><span data-stu-id="504aa-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="504aa-119">使用`val`關鍵字時，不會在建立物件時指定欄位的值，而是使用預設值來初始化。</span><span class="sxs-lookup"><span data-stu-id="504aa-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="504aa-120">如需詳細資訊, [請參閱明確欄位:Val 關鍵字](explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="504aa-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="504aa-121">您也可以使用成員定義來定義類別中的私用欄位，並將關鍵字`private`新增至定義。</span><span class="sxs-lookup"><span data-stu-id="504aa-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="504aa-122">如果您想要變更成員的存取範圍，而不需要重寫程式碼，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="504aa-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="504aa-123">如需詳細資訊，請參閱[存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="504aa-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="504aa-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="504aa-124">See also</span></span>

- [<span data-ttu-id="504aa-125">成員</span><span class="sxs-lookup"><span data-stu-id="504aa-125">Members</span></span>](index.md)
- [<span data-ttu-id="504aa-126">類別中的 `do` 繫結</span><span class="sxs-lookup"><span data-stu-id="504aa-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="504aa-127">`let`關係</span><span class="sxs-lookup"><span data-stu-id="504aa-127">`let` Bindings</span></span>](../functions/let-bindings.md)
