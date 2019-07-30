---
title: do 繫結
description: 瞭解如何使用F# 「do」系結來執行程式碼, 而不需要定義函數或值。
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630534"
---
# <a name="do-bindings"></a><span data-ttu-id="3801c-103">do 繫結</span><span class="sxs-lookup"><span data-stu-id="3801c-103">do Bindings</span></span>

<span data-ttu-id="3801c-104">`do`系結是用來執行程式碼, 而不需要定義函式或值。</span><span class="sxs-lookup"><span data-stu-id="3801c-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="3801c-105">此外, 您可以在類別中使用系結, 請參閱[ `do`類別中的](../members/do-bindings-in-classes.md)系結。</span><span class="sxs-lookup"><span data-stu-id="3801c-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="3801c-106">語法</span><span class="sxs-lookup"><span data-stu-id="3801c-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="3801c-107">備註</span><span class="sxs-lookup"><span data-stu-id="3801c-107">Remarks</span></span>

<span data-ttu-id="3801c-108">`do`當您想要獨立執行函式或值定義以外的程式碼時, 請使用系結。</span><span class="sxs-lookup"><span data-stu-id="3801c-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="3801c-109">系結中`do`的運算式`unit`必須傳回。</span><span class="sxs-lookup"><span data-stu-id="3801c-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="3801c-110">當模組初始化時, 會`do`執行最上層系結中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3801c-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="3801c-111">關鍵字`do`是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="3801c-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="3801c-112">屬性可以套用至最上層`do`系結。</span><span class="sxs-lookup"><span data-stu-id="3801c-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="3801c-113">例如, 如果您的程式使用 COM Interop, 您可能會想要將`STAThread`屬性套用至您的程式。</span><span class="sxs-lookup"><span data-stu-id="3801c-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="3801c-114">您可以使用系結上`do`的屬性來執行此動作, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="3801c-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="3801c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3801c-115">See also</span></span>

- [<span data-ttu-id="3801c-116">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="3801c-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="3801c-117">函式</span><span class="sxs-lookup"><span data-stu-id="3801c-117">Functions</span></span>](index.md)
