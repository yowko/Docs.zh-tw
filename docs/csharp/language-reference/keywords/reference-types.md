---
title: 參考型別 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744524"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="707da-102">參考類型 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="707da-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="707da-103">C# 中有兩種型別：參考型別和實值型別。</span><span class="sxs-lookup"><span data-stu-id="707da-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="707da-104">參考型別的變數會儲存對其資料 (物件) 的參考，而實值型別的變數則會直接包含其資料。</span><span class="sxs-lookup"><span data-stu-id="707da-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="707da-105">使用參考型別時，這兩個變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="707da-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="707da-106">使用實值型別時，每個變數都有自己的資料複本，因此對某一個變數進行的作業，不可能會影響其他變數 (但 in、ref 及 out 參數變數除外，請參閱 [in](in-parameter-modifier.md)、[ref](ref.md) 及 [out](out-parameter-modifier.md) 參數修飾詞)。</span><span class="sxs-lookup"><span data-stu-id="707da-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="707da-107">下列關鍵字用來宣告參考類型：</span><span class="sxs-lookup"><span data-stu-id="707da-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="707da-108">class</span><span class="sxs-lookup"><span data-stu-id="707da-108">class</span></span>](class.md)

- [<span data-ttu-id="707da-109">interface</span><span class="sxs-lookup"><span data-stu-id="707da-109">interface</span></span>](interface.md)

- [<span data-ttu-id="707da-110">delegate</span><span class="sxs-lookup"><span data-stu-id="707da-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="707da-111">C# 還提供下列內建參考類型：</span><span class="sxs-lookup"><span data-stu-id="707da-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="707da-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="707da-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="707da-113">object</span><span class="sxs-lookup"><span data-stu-id="707da-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="707da-114">string</span><span class="sxs-lookup"><span data-stu-id="707da-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="707da-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="707da-115">See also</span></span>

- [<span data-ttu-id="707da-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="707da-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="707da-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="707da-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="707da-118">指標型別</span><span class="sxs-lookup"><span data-stu-id="707da-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="707da-119">值類型</span><span class="sxs-lookup"><span data-stu-id="707da-119">Value types</span></span>](../builtin-types/value-types.md)
