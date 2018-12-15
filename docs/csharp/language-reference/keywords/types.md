---
title: 類型 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
ms.openlocfilehash: f5a3ad9fef108c1eec2ba63d68bc5015d2f6c430
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53142953"
---
# <a name="types-c-reference"></a><span data-ttu-id="f81ff-102">類型 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f81ff-102">Types (C# Reference)</span></span>

<span data-ttu-id="f81ff-103">C# 類型系統包含下列類別：</span><span class="sxs-lookup"><span data-stu-id="f81ff-103">The C# typing system contains the following categories:</span></span>

- [<span data-ttu-id="f81ff-104">實值型別</span><span class="sxs-lookup"><span data-stu-id="f81ff-104">Value types</span></span>](value-types.md)

- [<span data-ttu-id="f81ff-105">參考型別</span><span class="sxs-lookup"><span data-stu-id="f81ff-105">Reference types</span></span>](reference-types.md)

- [<span data-ttu-id="f81ff-106">指標型別</span><span class="sxs-lookup"><span data-stu-id="f81ff-106">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)

 <span data-ttu-id="f81ff-107">為實值型別的變數可儲存資料，而為參考型別的變數可儲存實際資料的參考。</span><span class="sxs-lookup"><span data-stu-id="f81ff-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="f81ff-108">參考型別的執行個體也稱為物件。</span><span class="sxs-lookup"><span data-stu-id="f81ff-108">Instances of reference types are also referred to as objects.</span></span> <span data-ttu-id="f81ff-109">指標類型只能用於 [unsafe](unsafe.md) 模式中。</span><span class="sxs-lookup"><span data-stu-id="f81ff-109">Pointer types can be used only in [unsafe](unsafe.md) mode.</span></span>

 <span data-ttu-id="f81ff-110">您可以使用 [boxing 和 unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)，將實值型別轉換成參考型別，然後再轉換回實值型別。</span><span class="sxs-lookup"><span data-stu-id="f81ff-110">It's possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="f81ff-111">除了 boxed 實值型別之外，您無法將參考型別轉換成實值型別。</span><span class="sxs-lookup"><span data-stu-id="f81ff-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>

 <span data-ttu-id="f81ff-112">本節也會介紹 [void](void.md)。</span><span class="sxs-lookup"><span data-stu-id="f81ff-112">This section also introduces [void](void.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f81ff-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f81ff-113">See also</span></span>

- [<span data-ttu-id="f81ff-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f81ff-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f81ff-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f81ff-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f81ff-116">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f81ff-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f81ff-117">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="f81ff-117">Reference Tables for Types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="f81ff-118">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="f81ff-118">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="f81ff-119">型別</span><span class="sxs-lookup"><span data-stu-id="f81ff-119">Types</span></span>](../../programming-guide/types/index.md)
