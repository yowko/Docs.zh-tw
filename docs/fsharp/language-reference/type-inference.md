---
title: "類型推斷 (F#)"
description: "了解 F # 編譯器推斷類型的值、 變數、 參數和傳回值的方式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2d5fa4b1-732a-4d71-a62d-07f7ee79fe06
ms.openlocfilehash: c23954c0a0828cc7d2aae0553d37d5ee1dfbe152
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="type-inference"></a><span data-ttu-id="b4d97-104">類型推斷</span><span class="sxs-lookup"><span data-stu-id="b4d97-104">Type Inference</span></span>

<span data-ttu-id="b4d97-105">本主題描述如何在 F # 編譯器會推斷值、 變數、 參數和傳回值的類型。</span><span class="sxs-lookup"><span data-stu-id="b4d97-105">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="b4d97-106">一般類型推斷</span><span class="sxs-lookup"><span data-stu-id="b4d97-106">Type Inference in General</span></span>
<span data-ttu-id="b4d97-107">型別推斷概念是，您不需要指定 F # 以外時，編譯器無法做出推算的類型建構的類型。</span><span class="sxs-lookup"><span data-stu-id="b4d97-107">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="b4d97-108">省略明確的型別資訊並不表示 F # 是動態類型的語言，或 F # 中的值是弱型別。</span><span class="sxs-lookup"><span data-stu-id="b4d97-108">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="b4d97-109">F # 是靜態類型的語言，這表示，編譯器會推算的確切每個建構類型，在編譯期間。</span><span class="sxs-lookup"><span data-stu-id="b4d97-109">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="b4d97-110">如果沒有足夠的資訊讓編譯器推斷每個建構類型，您必須在程式碼中某處加入明確的型別註解通常提供其他類型資訊。</span><span class="sxs-lookup"><span data-stu-id="b4d97-110">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>


## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="b4d97-111">參數和傳回型別推斷</span><span class="sxs-lookup"><span data-stu-id="b4d97-111">Inference of Parameter and Return Types</span></span>
<span data-ttu-id="b4d97-112">在參數清單中，您不必指定每個參數的型別。</span><span class="sxs-lookup"><span data-stu-id="b4d97-112">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="b4d97-113">和棒的是，F # 是靜態類型的語言，因此每個值與運算式具有明確類型在編譯時間。</span><span class="sxs-lookup"><span data-stu-id="b4d97-113">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="b4d97-114">針對未明確指定的類型，編譯器會推斷內容為基礎的類型。</span><span class="sxs-lookup"><span data-stu-id="b4d97-114">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="b4d97-115">如果類型不是其他指定，它會推斷為泛型。</span><span class="sxs-lookup"><span data-stu-id="b4d97-115">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="b4d97-116">如果程式碼會使用值不一致，這類方式沒有任何單一推斷滿足使用的所有值，編譯器會報告錯誤的類型。</span><span class="sxs-lookup"><span data-stu-id="b4d97-116">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="b4d97-117">函式的傳回型別取決於函式中的最後一個運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="b4d97-117">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="b4d97-118">例如，在下列程式碼的參數型別`a`和`b`和傳回型別會推斷為`int`因為常值`100`的型別`int`。</span><span class="sxs-lookup"><span data-stu-id="b4d97-118">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="b4d97-119">您可以藉由變更常值會影響型別推斷。</span><span class="sxs-lookup"><span data-stu-id="b4d97-119">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="b4d97-120">如果您進行`100``uint32`藉由附加後置詞`u`，類型的`a`， `b`，並傳回值會被推斷為`uint32`。</span><span class="sxs-lookup"><span data-stu-id="b4d97-120">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="b4d97-121">您可能也會影響使用的其他建構隱含限制的類型，例如函式和方法可搭配特定類型的型別推斷。</span><span class="sxs-lookup"><span data-stu-id="b4d97-121">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="b4d97-122">此外，您可以套用明確的類型註釋函式或方法參數或變數在運算式中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b4d97-122">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="b4d97-123">不同的條件約束之間發生衝突時，就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4d97-123">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="b4d97-124">您可以同時也可以明確指定函式的傳回值，藉由在所有參數提供型別附註。</span><span class="sxs-lookup"><span data-stu-id="b4d97-124">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="b4d97-125">常見的案例，其中類型註釋是有用的參數時，參數是物件類型，而且您想要使用的成員。</span><span class="sxs-lookup"><span data-stu-id="b4d97-125">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a><span data-ttu-id="b4d97-126">自動一般化</span><span class="sxs-lookup"><span data-stu-id="b4d97-126">Automatic Generalization</span></span>
<span data-ttu-id="b4d97-127">如果函式程式碼不是參數的類型而定，編譯器會考慮泛型參數。</span><span class="sxs-lookup"><span data-stu-id="b4d97-127">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="b4d97-128">這稱為*自動一般化*，而且它可以是功能強大的輔助工具，而不會增加複雜性撰寫泛型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4d97-128">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="b4d97-129">例如，下列函式結合成一個 tuple 的任何類型的兩個參數。</span><span class="sxs-lookup"><span data-stu-id="b4d97-129">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="b4d97-130">被推斷的類型</span><span class="sxs-lookup"><span data-stu-id="b4d97-130">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="b4d97-131">其他資訊</span><span class="sxs-lookup"><span data-stu-id="b4d97-131">Additional Information</span></span>
<span data-ttu-id="b4d97-132">F # 語言規格中的更詳細地描述型別推斷。</span><span class="sxs-lookup"><span data-stu-id="b4d97-132">Type inference is described in more detail in the F# Language Specification.</span></span>


## <a name="see-also"></a><span data-ttu-id="b4d97-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4d97-133">See Also</span></span>
[<span data-ttu-id="b4d97-134">自動一般化</span><span class="sxs-lookup"><span data-stu-id="b4d97-134">Automatic Generalization</span></span>](generics/automatic-generalization.md)
