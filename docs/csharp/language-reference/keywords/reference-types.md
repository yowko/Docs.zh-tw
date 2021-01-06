---
description: 參考型別 - C# 參考
title: 參考型別 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 075ec5ecd8f71f5cb85bab0e2baff56409709191
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899609"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="a6ac7-103">參考類型 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a6ac7-103">Reference types (C# Reference)</span></span>

<span data-ttu-id="a6ac7-104">C# 中有兩種類型：參考類型和實值類型。</span><span class="sxs-lookup"><span data-stu-id="a6ac7-104">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="a6ac7-105">參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。</span><span class="sxs-lookup"><span data-stu-id="a6ac7-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="a6ac7-106">使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="a6ac7-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="a6ac7-107">使用實值型別時，每個變數都有自己的資料複本，因此對某一個變數進行的作業，不可能會影響另一個變數 (但 in、ref 及 out 參數變數除外)，請參閱 [in](in-parameter-modifier.md)、[ref](ref.md) 及 [out](out-parameter-modifier.md) 參數修飾詞)。</span><span class="sxs-lookup"><span data-stu-id="a6ac7-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="a6ac7-108">下列關鍵字用來宣告參考型別：</span><span class="sxs-lookup"><span data-stu-id="a6ac7-108">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="a6ac7-109">class</span><span class="sxs-lookup"><span data-stu-id="a6ac7-109">class</span></span>](class.md)

- [<span data-ttu-id="a6ac7-110">interface</span><span class="sxs-lookup"><span data-stu-id="a6ac7-110">interface</span></span>](interface.md)

- [<span data-ttu-id="a6ac7-111">delegate</span><span class="sxs-lookup"><span data-stu-id="a6ac7-111">delegate</span></span>](../builtin-types/reference-types.md)
- [<span data-ttu-id="a6ac7-112">記錄</span><span class="sxs-lookup"><span data-stu-id="a6ac7-112">record</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="a6ac7-113">C# 還提供下列內建參考類型：</span><span class="sxs-lookup"><span data-stu-id="a6ac7-113">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="a6ac7-114">動態</span><span class="sxs-lookup"><span data-stu-id="a6ac7-114">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="a6ac7-115">object</span><span class="sxs-lookup"><span data-stu-id="a6ac7-115">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="a6ac7-116">string</span><span class="sxs-lookup"><span data-stu-id="a6ac7-116">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="a6ac7-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6ac7-117">See also</span></span>

- [<span data-ttu-id="a6ac7-118">C # 參考</span><span class="sxs-lookup"><span data-stu-id="a6ac7-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a6ac7-119">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a6ac7-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a6ac7-120">指標類型</span><span class="sxs-lookup"><span data-stu-id="a6ac7-120">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="a6ac7-121">值類型</span><span class="sxs-lookup"><span data-stu-id="a6ac7-121">Value types</span></span>](../builtin-types/value-types.md)
