---
title: 參考類型 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: cca9826c658581be38866410d5f966b1c7c35772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267335"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="1b1fb-102">參考類型 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1b1fb-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="1b1fb-103">C# 中有兩種類型：參考類型和實值類型。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="1b1fb-104">參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="1b1fb-105">使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="1b1fb-106">使用實值型別時，每個變數都有自己的資料複本，因此對某一個變數進行的作業，不可能會影響其他變數 (但 in、ref 及 out 參數變數除外，請參閱 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) 及 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數修飾詞)。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter modifier).</span></span>  
  
 <span data-ttu-id="1b1fb-107">下列關鍵字用來宣告參考類型：</span><span class="sxs-lookup"><span data-stu-id="1b1fb-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="1b1fb-108">class</span><span class="sxs-lookup"><span data-stu-id="1b1fb-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="1b1fb-109">interface</span><span class="sxs-lookup"><span data-stu-id="1b1fb-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="1b1fb-110">delegate</span><span class="sxs-lookup"><span data-stu-id="1b1fb-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="1b1fb-111">C# 還提供下列內建參考類型：</span><span class="sxs-lookup"><span data-stu-id="1b1fb-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="1b1fb-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="1b1fb-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="1b1fb-113">object</span><span class="sxs-lookup"><span data-stu-id="1b1fb-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="1b1fb-114">string</span><span class="sxs-lookup"><span data-stu-id="1b1fb-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b1fb-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b1fb-115">See Also</span></span>  
 [<span data-ttu-id="1b1fb-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1b1fb-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1b1fb-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1b1fb-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1b1fb-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1b1fb-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1b1fb-119">型別</span><span class="sxs-lookup"><span data-stu-id="1b1fb-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="1b1fb-120">實值型別</span><span class="sxs-lookup"><span data-stu-id="1b1fb-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
