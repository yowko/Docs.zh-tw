---
title: 基本資料類型
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: ae561bad3315977ba12dd0e12abda1da163ca456
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156013"
---
# <a name="basic-data-types"></a><span data-ttu-id="0b533-102">基本資料類型</span><span class="sxs-lookup"><span data-stu-id="0b533-102">Basic Data Types</span></span>

<span data-ttu-id="0b533-103">由於 LINQ to SQL 查詢會先轉譯成 Transact-SQL，然後才能在 Microsoft SQL Server 上執行。</span><span class="sxs-lookup"><span data-stu-id="0b533-103">Because LINQ to SQL queries translate to Transact-SQL before they are executed on the Microsoft SQL Server.</span></span> <span data-ttu-id="0b533-104">因此，在基本資料型別方面，LINQ to SQL 所支援的許多內建功能都與 SQL Server 相同。</span><span class="sxs-lookup"><span data-stu-id="0b533-104">LINQ to SQL supports much of the same built-in functionality that SQL Server does for basic data types.</span></span>  
  
## <a name="casting"></a><span data-ttu-id="0b533-105">轉型</span><span class="sxs-lookup"><span data-stu-id="0b533-105">Casting</span></span>  

 <span data-ttu-id="0b533-106">如果 SQL Server 內具有與來源 CLR 型別到目標 CLR 型別之隱含或明確轉換 (Cast) 類似的有效轉換，就會啟用這類隱含或明確轉換。</span><span class="sxs-lookup"><span data-stu-id="0b533-106">Implicit or explicit casts are enabled from a source CLR type to a target CLR type if there is a similar valid conversion within SQL Server.</span></span> <span data-ttu-id="0b533-107">如需有關 CLR 轉換的詳細資訊，請參閱 [CType 函數](../../../../../visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) 和 [類型測試和轉換運算子](../../../../../csharp/language-reference/operators/type-testing-and-cast.md)。</span><span class="sxs-lookup"><span data-stu-id="0b533-107">For more information about CLR casting, see [CType Function](../../../../../visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) and [Type-testing and cast operators](../../../../../csharp/language-reference/operators/type-testing-and-cast.md).</span></span> <span data-ttu-id="0b533-108">轉換 (Conversion) 之後，轉換 (Cast) 會變更 CLR 運算式上執行的作業行為，使其符合其他會自然對應至目的型別之 CLR 運算式的行為。</span><span class="sxs-lookup"><span data-stu-id="0b533-108">After conversion, casts change the behavior of operations performed on a CLR expression to match the behavior of other CLR expressions that naturally map to the destination type.</span></span> <span data-ttu-id="0b533-109">在繼承對應的內容中，轉換 (Cast) 也是可以轉譯的。</span><span class="sxs-lookup"><span data-stu-id="0b533-109">Casts are also translatable in the context of inheritance mapping.</span></span> <span data-ttu-id="0b533-110">物件可以轉換 (Cast) 為更特定的實體子型別，因此可以存取物件的子型別特定資料。</span><span class="sxs-lookup"><span data-stu-id="0b533-110">Objects can be cast to more specific entity subtypes so that their subtype-specific data can be accessed.</span></span>  
  
## <a name="equality-operators"></a><span data-ttu-id="0b533-111">相等運算子</span><span class="sxs-lookup"><span data-stu-id="0b533-111">Equality Operators</span></span>  

 <span data-ttu-id="0b533-112">LINQ to SQL 支援針對 LINQ to SQL 查詢內部的基本資料型別使用下列等號比較運算子：</span><span class="sxs-lookup"><span data-stu-id="0b533-112">LINQ to SQL supports the following equality operators on basic data types inside LINQ to SQL queries:</span></span>  
  
- <span data-ttu-id="0b533-113">等號和不等比較運算子：數值、 <xref:System.Boolean> 、和類型支援等號和不等比較運算子 <xref:System.DateTime> <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="0b533-113">Equal and Inequality Operator: Equality and inequality operators are supported for numeric, <xref:System.Boolean>, <xref:System.DateTime>, and <xref:System.TimeSpan> types.</span></span> <span data-ttu-id="0b533-114">如需 Visual Basic 運算子和的詳細資訊 `=` `<>` ，請參閱 [比較運算子](../../../../../visual-basic/language-reference/operators/comparison-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="0b533-114">For more about Visual Basic operators `=` and `<>`, see [Comparison Operators](../../../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span> <span data-ttu-id="0b533-115">如需 c # 比較運算子和的詳細資訊 `==` `!=` ，請參閱 [相等運算子](../../../../../csharp/language-reference/operators/equality-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="0b533-115">For more information about C# comparison operators `==` and `!=`, see [Equality operators](../../../../../csharp/language-reference/operators/equality-operators.md).</span></span>
  
- <span data-ttu-id="0b533-116">Is 運算子：使用繼承對應時，`IS` 運算子具有支援的轉譯。</span><span class="sxs-lookup"><span data-stu-id="0b533-116">Is operator: The `IS` operator has a supported translation when inheritance mapping is being used.</span></span> <span data-ttu-id="0b533-117">它可以用來判斷物件是否為特定實體型別，而且可以轉譯為鑑別子資料行上的檢查，而不需要直接測試鑑別子資料行。</span><span class="sxs-lookup"><span data-stu-id="0b533-117">It can be used instead of directly testing the discriminator column to determine whether an object is of a specific entity type, and is translated to a check on the discriminator column.</span></span> <span data-ttu-id="0b533-118">如需 Visual Basic 的詳細資訊，以及 c # 為運算子，請參閱 [是運算子](../../../../../visual-basic/language-reference/operators/is-operator.md) ，而且 [是](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator)。</span><span class="sxs-lookup"><span data-stu-id="0b533-118">For more information about the Visual Basic and C# Is operators, see [Is Operator](../../../../../visual-basic/language-reference/operators/is-operator.md) and [is](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b533-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b533-119">See also</span></span>

- [<span data-ttu-id="0b533-120">SQL-CLR 類型對應</span><span class="sxs-lookup"><span data-stu-id="0b533-120">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="0b533-121">資料類型與函式</span><span class="sxs-lookup"><span data-stu-id="0b533-121">Data Types and Functions</span></span>](data-types-and-functions.md)
