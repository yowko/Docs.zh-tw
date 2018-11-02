---
title: do 繫結 (F#)
description: "了解如何將 F # 'do' 繫結用來執行程式碼未定義的函式或值。"
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "45973140"
---
# <a name="do-bindings"></a><span data-ttu-id="04160-103">do 繫結</span><span class="sxs-lookup"><span data-stu-id="04160-103">do Bindings</span></span>

<span data-ttu-id="04160-104">A`do`繫結會用來執行程式碼，而不需定義的函式或值。</span><span class="sxs-lookup"><span data-stu-id="04160-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="04160-105">此外，執行繫結可以是在類別中使用，請參閱[`do`類別中的繫結](../members/do-bindings-in-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="04160-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="04160-106">語法</span><span class="sxs-lookup"><span data-stu-id="04160-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="04160-107">備註</span><span class="sxs-lookup"><span data-stu-id="04160-107">Remarks</span></span>

<span data-ttu-id="04160-108">使用`do`繫結，當您想要執行的函式或值的定義獨立的程式碼。</span><span class="sxs-lookup"><span data-stu-id="04160-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="04160-109">中的運算式`do`繫結必須傳回`unit`。</span><span class="sxs-lookup"><span data-stu-id="04160-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="04160-110">在最上層的程式碼`do`模組初始化時，會執行繫結。</span><span class="sxs-lookup"><span data-stu-id="04160-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="04160-111">關鍵字`do`是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="04160-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="04160-112">屬性可以套用至最上層`do`繫結。</span><span class="sxs-lookup"><span data-stu-id="04160-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="04160-113">比方說，如果您的程式使用 COM interop，您可能想要套用`STAThread`屬性設定為您的程式。</span><span class="sxs-lookup"><span data-stu-id="04160-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="04160-114">您可以使用屬性上`do`繫結，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="04160-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="04160-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04160-115">See also</span></span>

- [<span data-ttu-id="04160-116">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="04160-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="04160-117">函式</span><span class="sxs-lookup"><span data-stu-id="04160-117">Functions</span></span>](index.md)
