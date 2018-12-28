---
title: 類型推斷
description: 了解如何F#編譯器會推斷值、 變數、 參數和傳回值的類型。
ms.date: 05/16/2016
ms.openlocfilehash: 3e61d5c81fde0a48af66a47745123a842dc04cb1
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612786"
---
# <a name="type-inference"></a><span data-ttu-id="28f5c-103">類型推斷</span><span class="sxs-lookup"><span data-stu-id="28f5c-103">Type Inference</span></span>

<span data-ttu-id="28f5c-104">本主題描述如何F#編譯器會推斷值、 變數、 參數和傳回值的類型。</span><span class="sxs-lookup"><span data-stu-id="28f5c-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="28f5c-105">一般型別推斷</span><span class="sxs-lookup"><span data-stu-id="28f5c-105">Type Inference in General</span></span>

<span data-ttu-id="28f5c-106">型別推斷的概念是您沒有指定類型的F#建構，但當編譯器無法確定推算的類型。</span><span class="sxs-lookup"><span data-stu-id="28f5c-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="28f5c-107">省略明確的類型資訊並不表示F#是動態類型的語言或中的值F#是弱型別。</span><span class="sxs-lookup"><span data-stu-id="28f5c-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="28f5c-108">F#是靜態類型的語言，這表示編譯器會推斷每個建構的確實型別，在編譯期間。</span><span class="sxs-lookup"><span data-stu-id="28f5c-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="28f5c-109">如果沒有足夠的資訊讓編譯器推斷每個建構的類型，您必須藉由在程式碼中某處新增明確的型別註解通常提供額外的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="28f5c-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="28f5c-110">參數和傳回型別推斷</span><span class="sxs-lookup"><span data-stu-id="28f5c-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="28f5c-111">在參數清單中，您不必指定每個參數的型別。</span><span class="sxs-lookup"><span data-stu-id="28f5c-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="28f5c-112">和的是，F#是靜態類型的語言，並因此每個值與運算式有明確的類型在編譯時期。</span><span class="sxs-lookup"><span data-stu-id="28f5c-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="28f5c-113">對於您未明確指定這些型別，編譯器會推斷內容為基礎的類型。</span><span class="sxs-lookup"><span data-stu-id="28f5c-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="28f5c-114">如果類型不是其他方式指定，它會推斷為泛型。</span><span class="sxs-lookup"><span data-stu-id="28f5c-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="28f5c-115">如果程式碼會使用值不一致，一種都不是單一推斷符合定義之值的所有使用編譯器報告錯誤的類型。</span><span class="sxs-lookup"><span data-stu-id="28f5c-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="28f5c-116">函式的傳回型別取決於函式中的最後一個運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="28f5c-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="28f5c-117">例如，在下列程式碼的參數型別`a`並`b`和傳回型別會推斷為`int`因為常值`100`屬於類型`int`。</span><span class="sxs-lookup"><span data-stu-id="28f5c-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="28f5c-118">您可以藉由變更的常值會影響型別推斷。</span><span class="sxs-lookup"><span data-stu-id="28f5c-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="28f5c-119">若要`100``uint32`附加後置詞`u`，種`a`， `b`，並傳回值會被推斷為`uint32`。</span><span class="sxs-lookup"><span data-stu-id="28f5c-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="28f5c-120">您也可以影響使用隱含的類型，例如函式和方法可搭配特定類型的限制的其他建構型別推斷。</span><span class="sxs-lookup"><span data-stu-id="28f5c-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="28f5c-121">此外，您可以套用明確的型別註釋函式或方法參數或變數在運算式中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="28f5c-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="28f5c-122">如果不同的條件約束之間發生衝突，就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="28f5c-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="28f5c-123">您也可以明確指定函式的傳回值所提供的型別註釋在所有的參數。</span><span class="sxs-lookup"><span data-stu-id="28f5c-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="28f5c-124">參數是物件類型，且您想要使用的成員時，型別註釋會在參數上很實用的常見案例。</span><span class="sxs-lookup"><span data-stu-id="28f5c-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="28f5c-125">自動一般化</span><span class="sxs-lookup"><span data-stu-id="28f5c-125">Automatic Generalization</span></span>

<span data-ttu-id="28f5c-126">如果函式程式碼不相依於參數的型別，則編譯器會考慮為泛型參數。</span><span class="sxs-lookup"><span data-stu-id="28f5c-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="28f5c-127">這就叫做*自動一般化*，它可以是功能強大的輔助工具，來撰寫泛型程式碼，而不會增加複雜度。</span><span class="sxs-lookup"><span data-stu-id="28f5c-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="28f5c-128">例如，下列函式結合兩個參數轉換為 tuple 的任何類型。</span><span class="sxs-lookup"><span data-stu-id="28f5c-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="28f5c-129">型別推斷為</span><span class="sxs-lookup"><span data-stu-id="28f5c-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="28f5c-130">其他資訊</span><span class="sxs-lookup"><span data-stu-id="28f5c-130">Additional Information</span></span>

<span data-ttu-id="28f5c-131">型別推斷更詳細地說明F#語言規格。</span><span class="sxs-lookup"><span data-stu-id="28f5c-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="28f5c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28f5c-132">See also</span></span>

- [<span data-ttu-id="28f5c-133">自動一般化</span><span class="sxs-lookup"><span data-stu-id="28f5c-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)