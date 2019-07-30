---
title: 類型推斷
description: 瞭解F#編譯器如何推斷值、變數、參數和傳回值的類型。
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630190"
---
# <a name="type-inference"></a><span data-ttu-id="dfaef-103">類型推斷</span><span class="sxs-lookup"><span data-stu-id="dfaef-103">Type Inference</span></span>

<span data-ttu-id="dfaef-104">本主題描述F#編譯器如何推斷值、變數、參數和傳回值的類型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="dfaef-105">一般型別推斷</span><span class="sxs-lookup"><span data-stu-id="dfaef-105">Type Inference in General</span></span>

<span data-ttu-id="dfaef-106">類型推斷的概念是, 您不需要指定F#結構的類型, 除非編譯器無法最終推算類型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="dfaef-107">省略明確類型資訊並不表示是F#動態類型的語言, 或中F#的值是弱式類型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="dfaef-108">F#是靜態類型語言, 這表示編譯器會在編譯期間會推算每個結構的確切類型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="dfaef-109">如果沒有足夠的資訊可讓編譯器推算出每個結構的類型, 您就必須提供額外的類型資訊, 通常是在程式碼中的某處新增明確的類型注釋。</span><span class="sxs-lookup"><span data-stu-id="dfaef-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="dfaef-110">參數和傳回類型的推斷</span><span class="sxs-lookup"><span data-stu-id="dfaef-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="dfaef-111">在參數清單中, 您不需要指定每個參數的類型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="dfaef-112">此外, F#是靜態類型的語言, 因此每個值和運算式在編譯時期都有一個明確的類型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="dfaef-113">針對您未明確指定的類型, 編譯器會根據內容來推斷類型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="dfaef-114">如果未另行指定類型, 則會將它推斷為泛型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="dfaef-115">如果程式碼以不一致的方式使用值, 在這種情況下, 如果沒有任何單一推斷類型滿足值的所有使用, 編譯器就會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="dfaef-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="dfaef-116">函式的傳回型別是由函式中最後一個運算式的型別所決定。</span><span class="sxs-lookup"><span data-stu-id="dfaef-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="dfaef-117">例如, 在下列程式碼中, 參數類型`a`和`b`和傳回類型`int`都會推斷為, 因為常`100`值的類型`int`為。</span><span class="sxs-lookup"><span data-stu-id="dfaef-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="dfaef-118">您可以藉由變更常值來影響型別推斷。</span><span class="sxs-lookup"><span data-stu-id="dfaef-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="dfaef-119">如果您藉`uint32`由`100` `u`附加`b`尾碼來`uint32`建立, 則會將、和傳回值的類型推斷為。`a`</span><span class="sxs-lookup"><span data-stu-id="dfaef-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="dfaef-120">您也可以使用其他表示類型限制的結構 (例如僅適用于特定類型的函數和方法), 來影響型別推斷。</span><span class="sxs-lookup"><span data-stu-id="dfaef-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="dfaef-121">此外, 您可以將明確類型注釋套用至函式或方法參數或運算式中的變數, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="dfaef-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="dfaef-122">如果在不同的條件約束之間發生衝突, 則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="dfaef-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="dfaef-123">您也可以在所有參數之後提供類型注釋, 以明確指定函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="dfaef-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="dfaef-124">類型注釋對參數很有用的常見情況是, 當參數是物件類型, 而您想要使用成員時。</span><span class="sxs-lookup"><span data-stu-id="dfaef-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="dfaef-125">自動一般化</span><span class="sxs-lookup"><span data-stu-id="dfaef-125">Automatic Generalization</span></span>

<span data-ttu-id="dfaef-126">如果函式程式碼不相依于參數的類型, 則編譯器會將參數視為泛型。</span><span class="sxs-lookup"><span data-stu-id="dfaef-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="dfaef-127">這稱為「*自動一般化*」, 它可以是在不增加複雜度的情況下撰寫一般程式碼的強大輔助工具。</span><span class="sxs-lookup"><span data-stu-id="dfaef-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="dfaef-128">例如, 下列函式會將任何類型的兩個參數結合成一個元組。</span><span class="sxs-lookup"><span data-stu-id="dfaef-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="dfaef-129">類型會推斷為</span><span class="sxs-lookup"><span data-stu-id="dfaef-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="dfaef-130">其他資訊</span><span class="sxs-lookup"><span data-stu-id="dfaef-130">Additional Information</span></span>

<span data-ttu-id="dfaef-131">類型推斷會在F#語言規格中以更詳細的方式加以描述。</span><span class="sxs-lookup"><span data-stu-id="dfaef-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfaef-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfaef-132">See also</span></span>

- [<span data-ttu-id="dfaef-133">自動一般化</span><span class="sxs-lookup"><span data-stu-id="dfaef-133">Automatic Generalization</span></span>](./generics/automatic-generalization.md)
