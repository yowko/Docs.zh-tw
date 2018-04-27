---
title: 基本資料類型
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e88767bd478b4b59e8c395473cfd8a36aaf68f3b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="basic-data-types"></a><span data-ttu-id="b2534-102">基本資料類型</span><span class="sxs-lookup"><span data-stu-id="b2534-102">Basic Data Types</span></span>
<span data-ttu-id="b2534-103">由於 LINQ to SQL 查詢會先轉譯成 Transact-SQL，然後才能在 Microsoft SQL Server 上執行。</span><span class="sxs-lookup"><span data-stu-id="b2534-103">Because LINQ to SQL queries translate to Transact-SQL before they are executed on the Microsoft SQL Server.</span></span> <span data-ttu-id="b2534-104">因此，在基本資料型別方面，LINQ to SQL 所支援的許多內建功能都與 SQL Server 相同。</span><span class="sxs-lookup"><span data-stu-id="b2534-104">LINQ to SQL supports much of the same built-in functionality that SQL Server does for basic data types.</span></span>  
  
## <a name="casting"></a><span data-ttu-id="b2534-105">轉型</span><span class="sxs-lookup"><span data-stu-id="b2534-105">Casting</span></span>  
 <span data-ttu-id="b2534-106">如果 SQL Server 內具有與來源 CLR 型別到目標 CLR 型別之隱含或明確轉換 (Cast) 類似的有效轉換，就會啟用這類隱含或明確轉換。</span><span class="sxs-lookup"><span data-stu-id="b2534-106">Implicit or explicit casts are enabled from a source CLR type to a target CLR type if there is a similar valid conversion within SQL Server.</span></span> <span data-ttu-id="b2534-107">如需有關 CLR 轉換的詳細資訊，請參閱[CType 函式](~/docs/visual-basic/language-reference/functions/ctype-function.md)(Visual Basic) 和[為](~/docs/csharp/language-reference/keywords/as.md)。</span><span class="sxs-lookup"><span data-stu-id="b2534-107">For more information about CLR casting, see [CType Function](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) and [as](~/docs/csharp/language-reference/keywords/as.md).</span></span> <span data-ttu-id="b2534-108">轉換 (Conversion) 之後，轉換 (Cast) 會變更 CLR 運算式上執行的作業行為，使其符合其他會自然對應至目的型別之 CLR 運算式的行為。</span><span class="sxs-lookup"><span data-stu-id="b2534-108">After conversion, casts change the behavior of operations performed on a CLR expression to match the behavior of other CLR expressions that naturally map to the destination type.</span></span> <span data-ttu-id="b2534-109">在繼承對應的內容中，轉換 (Cast) 也是可以轉譯的。</span><span class="sxs-lookup"><span data-stu-id="b2534-109">Casts are also translatable in the context of inheritance mapping.</span></span> <span data-ttu-id="b2534-110">物件可以轉換 (Cast) 為更特定的實體子型別，因此可以存取物件的子型別特定資料。</span><span class="sxs-lookup"><span data-stu-id="b2534-110">Objects can be cast to more specific entity subtypes so that their subtype-specific data can be accessed.</span></span>  
  
## <a name="equality-operators"></a><span data-ttu-id="b2534-111">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="b2534-111">Equality Operators</span></span>  
 <span data-ttu-id="b2534-112">LINQ to SQL 支援針對 LINQ to SQL 查詢內部的基本資料型別使用下列等號比較運算子：</span><span class="sxs-lookup"><span data-stu-id="b2534-112">LINQ to SQL supports the following equality operators on basic data types inside LINQ to SQL queries:</span></span>  
  
-   <span data-ttu-id="b2534-113">等號和不等比較運算子：數值 <xref:System.Boolean>、<xref:System.DateTime> 和 <xref:System.TimeSpan> 型別都支援等號和不等比較運算子。</span><span class="sxs-lookup"><span data-stu-id="b2534-113">Equal and Inequality Operator: Equality and inequality operators are supported for numeric <xref:System.Boolean>, <xref:System.DateTime>, and <xref:System.TimeSpan> types.</span></span> <span data-ttu-id="b2534-114">如需詳細資訊 Visual Basic 運算子`=`和`<>`，請參閱[比較運算子](~/docs/visual-basic/language-reference/operators/comparison-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="b2534-114">For more about Visual Basic operators `=` and `<>`, see [Comparison Operators](~/docs/visual-basic/language-reference/operators/comparison-operators.md).</span></span> <span data-ttu-id="b2534-115">如需有關 C# 比較運算子`==`和`!=`，請參閱[= = 運算子](~/docs/csharp/language-reference/operators/equality-comparison-operator.md)和[！ = 運算子](~/docs/csharp/language-reference/operators/not-equal-operator.md)分別</span><span class="sxs-lookup"><span data-stu-id="b2534-115">For more information about C# comparison operators `==` and `!=`, see [== Operator](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) and [!= Operator](~/docs/csharp/language-reference/operators/not-equal-operator.md), respectively</span></span>  
  
-   <span data-ttu-id="b2534-116">Is 運算子：使用繼承對應時，`IS` 運算子具有支援的轉譯。</span><span class="sxs-lookup"><span data-stu-id="b2534-116">Is operator: The `IS` operator has a supported translation when inheritance mapping is being used.</span></span> <span data-ttu-id="b2534-117">它可以用來判斷物件是否為特定實體型別，而且可以轉譯為鑑別子資料行上的檢查，而不需要直接測試鑑別子資料行。</span><span class="sxs-lookup"><span data-stu-id="b2534-117">It can be used instead of directly testing the discriminator column to determine whether an object is of a specific entity type, and is translated to a check on the discriminator column.</span></span> <span data-ttu-id="b2534-118">如需 Visual Basic 和 C# 中是運算子的詳細資訊，請參閱[Is 運算子](~/docs/visual-basic/language-reference/operators/is-operator.md)和[是](~/docs/csharp/language-reference/keywords/is.md)。</span><span class="sxs-lookup"><span data-stu-id="b2534-118">For more information about the Visual Basic and C# Is operators, see [Is Operator](~/docs/visual-basic/language-reference/operators/is-operator.md) and [is](~/docs/csharp/language-reference/keywords/is.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2534-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2534-119">See Also</span></span>  
 [<span data-ttu-id="b2534-120">SQL-CLR 類型對應</span><span class="sxs-lookup"><span data-stu-id="b2534-120">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="b2534-121">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="b2534-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
