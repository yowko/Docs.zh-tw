---
title: "do 繫結 (F#)"
description: "了解如何 F # 'do' 繫結用來執行程式碼，但未定義函式或值。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings"></a><span data-ttu-id="32242-104">do 繫結</span><span class="sxs-lookup"><span data-stu-id="32242-104">do Bindings</span></span>

<span data-ttu-id="32242-105">A`do`繫結會用來執行程式碼，但未定義函式或值。</span><span class="sxs-lookup"><span data-stu-id="32242-105">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="32242-106">此外，請勿繫結可以是在類別中使用，請參閱[`do`類別中的繫結](../members/do-bindings-in-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="32242-106">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="32242-107">語法</span><span class="sxs-lookup"><span data-stu-id="32242-107">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="32242-108">備註</span><span class="sxs-lookup"><span data-stu-id="32242-108">Remarks</span></span>
<span data-ttu-id="32242-109">使用`do`繫結，當您想要執行的函式或值的定義獨立的程式碼。</span><span class="sxs-lookup"><span data-stu-id="32242-109">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="32242-110">中的運算式`do`繫結必須傳回`unit`。</span><span class="sxs-lookup"><span data-stu-id="32242-110">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="32242-111">程式碼中的最上層`do`模組初始化時，會執行繫結。</span><span class="sxs-lookup"><span data-stu-id="32242-111">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="32242-112">關鍵字`do`是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="32242-112">The keyword `do` is optional.</span></span>

<span data-ttu-id="32242-113">屬性可以套用至最上層`do`繫結。</span><span class="sxs-lookup"><span data-stu-id="32242-113">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="32242-114">例如，如果您的程式使用 COM interop，您可能要套用`STAThread`屬性加入您的程式。</span><span class="sxs-lookup"><span data-stu-id="32242-114">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="32242-115">您可以使用屬性上`do`繫結，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="32242-115">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="32242-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32242-116">See Also</span></span>
[<span data-ttu-id="32242-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="32242-117">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="32242-118">函式</span><span class="sxs-lookup"><span data-stu-id="32242-118">Functions</span></span>](index.md)

