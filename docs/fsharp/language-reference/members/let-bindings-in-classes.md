---
title: 類別中的 let 繫結 (F#)
description: "了解如何在類別定義中使用 'let' 的繫結來定義私用欄位和 F # 類別的私用函式。"
ms.date: 05/16/2016
ms.openlocfilehash: 237eb98a57571a21c9187abf31f05160374cf4fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186015"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="a89aa-103">類別中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="a89aa-103">let Bindings in Classes</span></span>

<span data-ttu-id="a89aa-104">您可以定義私用欄位和 F # 類別的私用函式使用`let`類別定義中的繫結。</span><span class="sxs-lookup"><span data-stu-id="a89aa-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="a89aa-105">語法</span><span class="sxs-lookup"><span data-stu-id="a89aa-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="a89aa-106">備註</span><span class="sxs-lookup"><span data-stu-id="a89aa-106">Remarks</span></span>

<span data-ttu-id="a89aa-107">類別標題和繼承宣告之後，但任何成員定義之前，會顯示先前的語法。</span><span class="sxs-lookup"><span data-stu-id="a89aa-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="a89aa-108">語法是類似`let`類別，但在類別中定義的名稱以外的繫結需要僅限於此類別的範圍。</span><span class="sxs-lookup"><span data-stu-id="a89aa-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="a89aa-109">A`let`繫結會建立私用欄位或函式; 將資料公開或公開，函式宣告的屬性或成員方法。</span><span class="sxs-lookup"><span data-stu-id="a89aa-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="a89aa-110">A`let`繫結，不是靜態的執行個體稱為`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="a89aa-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="a89aa-111">執行個體`let`繫結執行建立物件時。</span><span class="sxs-lookup"><span data-stu-id="a89aa-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="a89aa-112">靜態`let`繫結是執行之前先使用的型別類別的靜態初始設定式的一部分。</span><span class="sxs-lookup"><span data-stu-id="a89aa-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="a89aa-113">執行個體中的程式碼`let`繫結可以使用主要建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="a89aa-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="a89aa-114">上不允許屬性和存取範圍修飾詞`let`類別中的繫結。</span><span class="sxs-lookup"><span data-stu-id="a89aa-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="a89aa-115">下列程式碼範例將說明數種`let`類別中的繫結。</span><span class="sxs-lookup"><span data-stu-id="a89aa-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="a89aa-116">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a89aa-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="a89aa-117">若要建立欄位的替代方式</span><span class="sxs-lookup"><span data-stu-id="a89aa-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="a89aa-118">您也可以使用`val`關鍵字來建立私用欄位。</span><span class="sxs-lookup"><span data-stu-id="a89aa-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="a89aa-119">當使用`val`關鍵字，欄位未指定值，當物件建立時，但改為使用預設值初始化。</span><span class="sxs-lookup"><span data-stu-id="a89aa-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="a89aa-120">如需詳細資訊，請參閱 <<c0> [ 明確欄位： val 關鍵字](explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="a89aa-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="a89aa-121">您也可以定義類別中私用欄位，藉由使用成員定義，以及加入關鍵字`private`的定義。</span><span class="sxs-lookup"><span data-stu-id="a89aa-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="a89aa-122">這可以是成員的很有用，如果您預期要變更存取範圍，而不需要重新撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="a89aa-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="a89aa-123">如需詳細資訊，請參閱[存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a89aa-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a89aa-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a89aa-124">See also</span></span>

- [<span data-ttu-id="a89aa-125">成員</span><span class="sxs-lookup"><span data-stu-id="a89aa-125">Members</span></span>](index.md)
- [<span data-ttu-id="a89aa-126">類別中的 `do` 繫結</span><span class="sxs-lookup"><span data-stu-id="a89aa-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="a89aa-127">`let` 繫結</span><span class="sxs-lookup"><span data-stu-id="a89aa-127">`let` Bindings</span></span>](../functions/let-bindings.md)
