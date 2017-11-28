---
title: "類型 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c7285e237b04c1290391c4bba3e62886dceb83c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="types-c-reference"></a><span data-ttu-id="aae35-102">類型 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="aae35-102">Types (C# Reference)</span></span>
<span data-ttu-id="aae35-103">C# 類型系統包含下列類別：</span><span class="sxs-lookup"><span data-stu-id="aae35-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="aae35-104">實值型別</span><span class="sxs-lookup"><span data-stu-id="aae35-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="aae35-105">參考型別</span><span class="sxs-lookup"><span data-stu-id="aae35-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="aae35-106">指標型別</span><span class="sxs-lookup"><span data-stu-id="aae35-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="aae35-107">為實值型別的變數可儲存資料，而為參考型別的變數可儲存實際資料的參考。</span><span class="sxs-lookup"><span data-stu-id="aae35-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="aae35-108">參考型別也稱為物件。</span><span class="sxs-lookup"><span data-stu-id="aae35-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="aae35-109">指標類型只能用於 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 模式中。</span><span class="sxs-lookup"><span data-stu-id="aae35-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="aae35-110">您可以使用 [boxing 和 unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)，將實值型別轉換成參考型別，然後再次轉換成實值型別。</span><span class="sxs-lookup"><span data-stu-id="aae35-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="aae35-111">除了 boxed 實值型別之外，您無法將參考型別轉換成實值型別。</span><span class="sxs-lookup"><span data-stu-id="aae35-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="aae35-112">本節也會介紹 [void](../../../csharp/language-reference/keywords/void.md)。</span><span class="sxs-lookup"><span data-stu-id="aae35-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="aae35-113">實值型別也可為 Null，這表示它們可以儲存額外的非值狀態。</span><span class="sxs-lookup"><span data-stu-id="aae35-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="aae35-114">如需詳細資訊，請參閱[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="aae35-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae35-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aae35-115">See Also</span></span>  
 [<span data-ttu-id="aae35-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="aae35-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aae35-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="aae35-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aae35-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="aae35-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="aae35-119">型別的參考表</span><span class="sxs-lookup"><span data-stu-id="aae35-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="aae35-120">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="aae35-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="aae35-121">型別</span><span class="sxs-lookup"><span data-stu-id="aae35-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
