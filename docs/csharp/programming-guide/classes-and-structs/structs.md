---
title: 結構 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 063d7e3b68fbe6c01ff0df4ae935fec5af6f6891
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743844"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="3ba2c-102">結構 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3ba2c-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="3ba2c-103">您可以使用 [struct](../../language-reference/keywords/struct.md) 關鍵字來定義結構，例如：</span><span class="sxs-lookup"><span data-stu-id="3ba2c-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
<span data-ttu-id="3ba2c-104">Struct 大部分與 class 共用相同語法。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="3ba2c-105">結構的名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="3ba2c-106">Struct 的限制在下列各方面比 class 多：</span><span class="sxs-lookup"><span data-stu-id="3ba2c-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="3ba2c-107">在結構宣告內，除非欄位宣告為常數或靜態，否則無法初始化欄位。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="3ba2c-108">結構無法宣告無參數建構函式 (不含參數的建構函式) 或完成項。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-108">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="3ba2c-109">指派時會複製結構。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-109">Structs are copied on assignment.</span></span> <span data-ttu-id="3ba2c-110">將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="3ba2c-111">使用 `Dictionary<string, myStruct>` 這類實值型別的集合時，請務必記住。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="3ba2c-112">Struct 是實值型別，不像 class 是參考型別。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="3ba2c-113">不同於類別，結構不需要使用 `new` 運算子就能具現化。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="3ba2c-114">結構可以宣告具有參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-114">Structs can declare constructors that have parameters.</span></span>
- <span data-ttu-id="3ba2c-115">結構無法繼承自另一個結構或類別，而且不能作為類別的基底。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="3ba2c-116">所有結構都直接繼承自 <xref:System.ValueType>，該項則繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="3ba2c-117">結構可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-117">A struct can implement interfaces.</span></span>
- <span data-ttu-id="3ba2c-118">結構不能是 `null`，而且除非將結構變數宣告為可為 Null 的型別，否則無法將 `null` 指派給該型別。</span><span class="sxs-lookup"><span data-stu-id="3ba2c-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable type.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3ba2c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ba2c-119">See also</span></span>

- [<span data-ttu-id="3ba2c-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3ba2c-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3ba2c-121">類別和結構</span><span class="sxs-lookup"><span data-stu-id="3ba2c-121">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="3ba2c-122">類別</span><span class="sxs-lookup"><span data-stu-id="3ba2c-122">Classes</span></span>](classes.md)
- [<span data-ttu-id="3ba2c-123">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="3ba2c-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="3ba2c-124">識別碼名稱</span><span class="sxs-lookup"><span data-stu-id="3ba2c-124">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="3ba2c-125">使用結構</span><span class="sxs-lookup"><span data-stu-id="3ba2c-125">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="3ba2c-126">如何：了解將結構和類別參考傳遞給方法之間的差異</span><span class="sxs-lookup"><span data-stu-id="3ba2c-126">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
