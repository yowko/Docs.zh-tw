---
title: 運算子宣告必須是下列其中一個： +,-, *,-,-, ^、 &amp; 、Like、Mod、And、Or、Xor、Not、 <<、 >>、=、 <>、<、<=、>、>=、CType、IsTrue、IsFalse
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: a94e62e33427987a302a6244b2b8ce8d295e4f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159894"
---
# <a name="bc33000-operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="5865f-102">BC33000：運算子宣告必須是下列其中一個： +,-, \*、 \, /、^、 &amp; 、Like、Mod、And、Or、Xor、Not、 \<\<, >> .。。</span><span class="sxs-lookup"><span data-stu-id="5865f-102">BC33000: Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>

<span data-ttu-id="5865f-103">您只能宣告有資格進行多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="5865f-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="5865f-104">下表列出您可以宣告的運算子。</span><span class="sxs-lookup"><span data-stu-id="5865f-104">The following table lists the operators you can declare.</span></span>

|<span data-ttu-id="5865f-105">類型</span><span class="sxs-lookup"><span data-stu-id="5865f-105">Type</span></span>|<span data-ttu-id="5865f-106">運算子</span><span class="sxs-lookup"><span data-stu-id="5865f-106">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="5865f-107">一元</span><span class="sxs-lookup"><span data-stu-id="5865f-107">Unary</span></span>|<span data-ttu-id="5865f-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="5865f-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="5865f-109">Binary</span><span class="sxs-lookup"><span data-stu-id="5865f-109">Binary</span></span>|<span data-ttu-id="5865f-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="5865f-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="5865f-111">轉換 (一元)</span><span class="sxs-lookup"><span data-stu-id="5865f-111">Conversion (unary)</span></span>|`CType`|

 <span data-ttu-id="5865f-112">請注意， `=` 二進位清單中的運算子是比較運算子，而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="5865f-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="5865f-113">**錯誤識別碼：** BC33000</span><span class="sxs-lookup"><span data-stu-id="5865f-113">**Error ID:** BC33000</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5865f-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5865f-114">To correct this error</span></span>

- <span data-ttu-id="5865f-115">從一組可多載的運算子中選取運算子。</span><span class="sxs-lookup"><span data-stu-id="5865f-115">Select an operator from the set of overloadable operators.</span></span>

- <span data-ttu-id="5865f-116">如果您需要多載無法直接多載之運算子的功能，請建立接受適當參數並傳回適當值的 `Function` 程序。</span><span class="sxs-lookup"><span data-stu-id="5865f-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>

## <a name="see-also"></a><span data-ttu-id="5865f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5865f-117">See also</span></span>

- [<span data-ttu-id="5865f-118">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="5865f-118">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="5865f-119">運算子程序</span><span class="sxs-lookup"><span data-stu-id="5865f-119">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="5865f-120">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="5865f-120">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="5865f-121">How to: Define a Conversion Operator</span><span class="sxs-lookup"><span data-stu-id="5865f-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="5865f-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="5865f-122">Function Statement</span></span>](../statements/function-statement.md)
