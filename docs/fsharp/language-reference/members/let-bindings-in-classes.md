---
title: 類別中的 let 繫結 (F#)
description: "了解如何在類別定義中使用 'let' 繫結定義私用欄位和 F # 類別的私用函式。"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c4511a541403dde517acaf902e86de8d48f13781
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="e1a96-103">類別中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="e1a96-103">let Bindings in Classes</span></span>

<span data-ttu-id="e1a96-104">您可以藉由定義私用欄位和 F # 類別的私用函式`let`類別定義中的繫結。</span><span class="sxs-lookup"><span data-stu-id="e1a96-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>


## <a name="syntax"></a><span data-ttu-id="e1a96-105">語法</span><span class="sxs-lookup"><span data-stu-id="e1a96-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="e1a96-106">備註</span><span class="sxs-lookup"><span data-stu-id="e1a96-106">Remarks</span></span>
<span data-ttu-id="e1a96-107">之後，類別標題和繼承的宣告，但任何成員定義之前，會顯示先前的語法。</span><span class="sxs-lookup"><span data-stu-id="e1a96-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="e1a96-108">語法是類似`let`外部類別，但類別中定義的名稱的繫結已限制為類別的範圍。</span><span class="sxs-lookup"><span data-stu-id="e1a96-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="e1a96-109">A`let`繫結會建立私用欄位或函式; 若要公開的資料或函式公開，宣告屬性或成員方法。</span><span class="sxs-lookup"><span data-stu-id="e1a96-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="e1a96-110">A`let`繫結，不是靜態的執行個體稱為`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="e1a96-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="e1a96-111">執行個體`let`繫結執行時，會建立物件。</span><span class="sxs-lookup"><span data-stu-id="e1a96-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="e1a96-112">靜態`let`繫結是類別，可保證執行之前先使用該類型的靜態初始設定式的一部分。</span><span class="sxs-lookup"><span data-stu-id="e1a96-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="e1a96-113">執行個體中的程式碼`let`繫結可以使用主要建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="e1a96-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="e1a96-114">上不允許屬性和存取範圍修飾詞`let`類別中的繫結。</span><span class="sxs-lookup"><span data-stu-id="e1a96-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="e1a96-115">下列程式碼範例將說明幾種類型的`let`類別中的繫結。</span><span class="sxs-lookup"><span data-stu-id="e1a96-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="e1a96-116">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="e1a96-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="e1a96-117">若要建立欄位的替代方式</span><span class="sxs-lookup"><span data-stu-id="e1a96-117">Alternative Ways to Create Fields</span></span>
<span data-ttu-id="e1a96-118">您也可以使用`val`關鍵字建立私用欄位。</span><span class="sxs-lookup"><span data-stu-id="e1a96-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="e1a96-119">當使用`val`關鍵字，欄位未指定值時，該物件會建立，但改為使用預設值初始化。</span><span class="sxs-lookup"><span data-stu-id="e1a96-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="e1a96-120">如需詳細資訊，請參閱[明確欄位： val 關鍵字](explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a96-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="e1a96-121">您也可以定義類別中的私用欄位，使用成員定義，並將關鍵字加入`private`的定義。</span><span class="sxs-lookup"><span data-stu-id="e1a96-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="e1a96-122">這很有用，如果您要變更成員的存取範圍，而不用重寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1a96-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="e1a96-123">如需詳細資訊，請參閱[存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a96-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1a96-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1a96-124">See Also</span></span>
[<span data-ttu-id="e1a96-125">成員</span><span class="sxs-lookup"><span data-stu-id="e1a96-125">Members</span></span>](index.md)

[<span data-ttu-id="e1a96-126">類別中的 `do` 繫結</span><span class="sxs-lookup"><span data-stu-id="e1a96-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)

[<span data-ttu-id="e1a96-127">`let` 繫結</span><span class="sxs-lookup"><span data-stu-id="e1a96-127">`let` Bindings</span></span>](../functions/let-bindings.md)
