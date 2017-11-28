---
title: "轉換運算子 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5277c1160c604ee56ff575df5bd603e115588d21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="b46ff-102">轉換運算子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b46ff-102">Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="b46ff-103">C# 可讓程式設計人員宣告類別或結構轉換，使類別或結構能夠與其他類別、結構或基本類型相互轉換。</span><span class="sxs-lookup"><span data-stu-id="b46ff-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="b46ff-104">轉換的定義方式類似運算子，並會以轉換的目標類型命名。</span><span class="sxs-lookup"><span data-stu-id="b46ff-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="b46ff-105">在引數所要轉換的目標類型或轉換的結果類型中，必須有一個是包含類型，但不能兩者都是。</span><span class="sxs-lookup"><span data-stu-id="b46ff-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="b46ff-106">轉換運算子概觀</span><span class="sxs-lookup"><span data-stu-id="b46ff-106">Conversion Operators Overview</span></span>  
 <span data-ttu-id="b46ff-107">轉換運算子具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b46ff-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="b46ff-108">宣告為 `implicit` 的轉換會在必要時自動發生。</span><span class="sxs-lookup"><span data-stu-id="b46ff-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="b46ff-109">宣告為 `explicit` 的轉換需要呼叫轉換。</span><span class="sxs-lookup"><span data-stu-id="b46ff-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="b46ff-110">所有轉換都必須宣告為 `static`。</span><span class="sxs-lookup"><span data-stu-id="b46ff-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b46ff-111">相關章節</span><span class="sxs-lookup"><span data-stu-id="b46ff-111">Related Sections</span></span>  
 <span data-ttu-id="b46ff-112">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="b46ff-112">For more information:</span></span>  
  
-   [<span data-ttu-id="b46ff-113">使用轉換運算子</span><span class="sxs-lookup"><span data-stu-id="b46ff-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="b46ff-114">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="b46ff-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="b46ff-115">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="b46ff-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="b46ff-116">explicit</span><span class="sxs-lookup"><span data-stu-id="b46ff-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="b46ff-117">implicit</span><span class="sxs-lookup"><span data-stu-id="b46ff-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="b46ff-118">static</span><span class="sxs-lookup"><span data-stu-id="b46ff-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="b46ff-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b46ff-119">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="b46ff-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b46ff-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b46ff-121">C# 中鏈結的使用者定義明確轉換</span><span class="sxs-lookup"><span data-stu-id="b46ff-121">Chained user-defined explicit conversions in C#</span></span>](http://go.microsoft.com/fwlink/?LinkId=112384)
