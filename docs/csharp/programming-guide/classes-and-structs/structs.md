---
title: 結構 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322984"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="31e45-102">結構 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="31e45-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="31e45-103">您可以使用 [struct](../../../csharp/language-reference/keywords/struct.md) 關鍵字來定義結構，例如：</span><span class="sxs-lookup"><span data-stu-id="31e45-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="31e45-104">結構與類別共用大部分相同的語法，不過結構的限制高於類別︰</span><span class="sxs-lookup"><span data-stu-id="31e45-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="31e45-105">在結構宣告內，除非欄位宣告為常數或靜態，否則無法初始化欄位。</span><span class="sxs-lookup"><span data-stu-id="31e45-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="31e45-106">結構無法宣告預設建構函式 (不含參數的建構函式) 或完成項。</span><span class="sxs-lookup"><span data-stu-id="31e45-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="31e45-107">指派時會複製結構。</span><span class="sxs-lookup"><span data-stu-id="31e45-107">Structs are copied on assignment.</span></span> <span data-ttu-id="31e45-108">將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。</span><span class="sxs-lookup"><span data-stu-id="31e45-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="31e45-109">使用實值型別集合 (例如 Dictionary\<string, myStruct>) 時，請一定要記住這一點。</span><span class="sxs-lookup"><span data-stu-id="31e45-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="31e45-110">結構是實值型別，而類別是參考型別。</span><span class="sxs-lookup"><span data-stu-id="31e45-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="31e45-111">不同於類別，結構不需要使用 `new` 運算子就能具現化。</span><span class="sxs-lookup"><span data-stu-id="31e45-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="31e45-112">結構可以宣告具有參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="31e45-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="31e45-113">結構無法繼承自另一個結構或類別，而且不能作為類別的基底。</span><span class="sxs-lookup"><span data-stu-id="31e45-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="31e45-114">所有結構都直接繼承自 `System.ValueType`，該項則繼承自 `System.Object`。</span><span class="sxs-lookup"><span data-stu-id="31e45-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="31e45-115">結構可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="31e45-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="31e45-116">結構可用作可為 Null 的型別，並可指派 Null 值。</span><span class="sxs-lookup"><span data-stu-id="31e45-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="31e45-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="31e45-117">Related Sections</span></span>  
 <span data-ttu-id="31e45-118">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="31e45-118">For more information:</span></span>  
  
-   [<span data-ttu-id="31e45-119">使用結構</span><span class="sxs-lookup"><span data-stu-id="31e45-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="31e45-120">建構函式</span><span class="sxs-lookup"><span data-stu-id="31e45-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="31e45-121">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="31e45-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="31e45-122">如何：了解將結構和類別參考傳遞給方法之間的差異</span><span class="sxs-lookup"><span data-stu-id="31e45-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="31e45-123">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="31e45-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="31e45-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="31e45-124">See Also</span></span>  
 [<span data-ttu-id="31e45-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="31e45-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="31e45-126">類別和結構</span><span class="sxs-lookup"><span data-stu-id="31e45-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="31e45-127">類別</span><span class="sxs-lookup"><span data-stu-id="31e45-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
