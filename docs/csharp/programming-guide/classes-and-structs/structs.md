---
title: 結構 (C# 程式設計手冊)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 27d4b0d7edf1b5e89e84ac1df5783d68ebb4efe0
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259480"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="510cd-102">結構 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="510cd-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="510cd-103">您可以使用 [struct](../../language-reference/keywords/struct.md) 關鍵字來定義結構，例如：</span><span class="sxs-lookup"><span data-stu-id="510cd-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="510cd-104">Struct 大部分與 class 共用相同語法。</span><span class="sxs-lookup"><span data-stu-id="510cd-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="510cd-105">結構的名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。</span><span class="sxs-lookup"><span data-stu-id="510cd-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="510cd-106">Struct 的限制在下列各方面比 class 多：</span><span class="sxs-lookup"><span data-stu-id="510cd-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="510cd-107">在結構宣告內，除非欄位宣告為常數或靜態，否則無法初始化欄位。</span><span class="sxs-lookup"><span data-stu-id="510cd-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="510cd-108">結構無法宣告預設建構函式 (不含參數的建構函式) 或完成項。</span><span class="sxs-lookup"><span data-stu-id="510cd-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="510cd-109">指派時會複製結構。</span><span class="sxs-lookup"><span data-stu-id="510cd-109">Structs are copied on assignment.</span></span> <span data-ttu-id="510cd-110">將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。</span><span class="sxs-lookup"><span data-stu-id="510cd-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="510cd-111">使用 `Dictionary<string, myStruct>` 這類實值型別的集合時，請務必記住。</span><span class="sxs-lookup"><span data-stu-id="510cd-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="510cd-112">Struct 是實值型別，不像 class 是參考型別。</span><span class="sxs-lookup"><span data-stu-id="510cd-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="510cd-113">不同於類別，結構不需要使用 `new` 運算子就能具現化。</span><span class="sxs-lookup"><span data-stu-id="510cd-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="510cd-114">結構可以宣告具有參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="510cd-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="510cd-115">結構無法繼承自另一個結構或類別，而且不能作為類別的基底。</span><span class="sxs-lookup"><span data-stu-id="510cd-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="510cd-116">所有結構都直接繼承自 <xref:System.ValueType>，該項則繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="510cd-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="510cd-117">結構可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="510cd-117">A struct can implement interfaces.</span></span>  
- <span data-ttu-id="510cd-118">結構可用作可為 Null 的型別，並可指派 Null 值。</span><span class="sxs-lookup"><span data-stu-id="510cd-118">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="510cd-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="510cd-119">Related sections</span></span>  

<span data-ttu-id="510cd-120">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="510cd-120">For more information:</span></span>  
  
- [<span data-ttu-id="510cd-121">使用結構</span><span class="sxs-lookup"><span data-stu-id="510cd-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="510cd-122">建構函式</span><span class="sxs-lookup"><span data-stu-id="510cd-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="510cd-123">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="510cd-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="510cd-124">如何：了解將結構和類別參考傳遞給方法之間的差異</span><span class="sxs-lookup"><span data-stu-id="510cd-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="510cd-125">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="510cd-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="510cd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="510cd-126">See also</span></span>

- [<span data-ttu-id="510cd-127">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="510cd-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="510cd-128">類別和結構</span><span class="sxs-lookup"><span data-stu-id="510cd-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="510cd-129">類別</span><span class="sxs-lookup"><span data-stu-id="510cd-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="510cd-130">識別碼名稱</span><span class="sxs-lookup"><span data-stu-id="510cd-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
