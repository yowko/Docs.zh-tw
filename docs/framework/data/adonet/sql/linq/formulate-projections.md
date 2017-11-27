---
title: "制定投影"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8afd48c6ce7c6313e82a7b74c2271f52833d1f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="formulate-projections"></a><span data-ttu-id="ee6d9-102">制定投影</span><span class="sxs-lookup"><span data-stu-id="ee6d9-102">Formulate Projections</span></span>
<span data-ttu-id="ee6d9-103">下列範例顯示 C# 中的 `select` 陳述式和 `Select` 中的 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 陳述式如何與其他功能結合，以構成查詢投影。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-103">The following examples show how the `select` statement in C# and `Select` statement in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee6d9-104">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-104">Example</span></span>  
 <span data-ttu-id="ee6d9-105">下列範例會使用`Select`中的子句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`子句在 C# 中的) 以傳回的連絡人名稱序列`Customers`。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-105">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="ee6d9-106">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-106">Example</span></span>  
 <span data-ttu-id="ee6d9-107">下列範例會使用`Select`中的子句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`子句在 C# 中的) 和*匿名型別*要傳回的連絡人名稱序列和電話號碼`Customers`。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-107">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="ee6d9-108">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-108">Example</span></span>  
 <span data-ttu-id="ee6d9-109">下列範例會使用`Select`中的子句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`子句在 C# 中的) 和*匿名型別*傳回一連串的名稱，並為員工電話號碼。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-109">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="ee6d9-110">`FirstName`和`LastName`欄位會合併成單一欄位 (`Name`)，而`HomePhone`欄位重新命名為`Phone`中所產生的順序。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="ee6d9-111">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-111">Example</span></span>  
 <span data-ttu-id="ee6d9-112">下列範例會使用`Select`中的子句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`子句在 C# 中的) 和*匿名型別*以傳回所有序列`ProductID`s 和名為的導出的值`HalfPrice`。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-112">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="ee6d9-113">此值設為 `UnitPrice` 除以 2。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="ee6d9-114">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-114">Example</span></span>  
 <span data-ttu-id="ee6d9-115">下列範例會使用`Select`中的子句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`子句在 C# 中的) 和*條件陳述式*傳回一連串的產品名稱和產品可用性。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-115">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="ee6d9-116">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-116">Example</span></span>  
 <span data-ttu-id="ee6d9-117">下列範例會使用[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]`Select`子句 (`select`子句在 C# 中的) 和*已知型別*(Name)，傳回員工的名稱的序列。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-117">The following example uses a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="ee6d9-118">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-118">Example</span></span>  
 <span data-ttu-id="ee6d9-119">下列範例會使用`Select`和`Where`中[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`和`where`C# 中) 來傳回*篩選順序*位於倫敦的客戶的連絡人名稱。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-119">The following example uses `Select` and `Where` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="ee6d9-120">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-120">Example</span></span>  
 <span data-ttu-id="ee6d9-121">下列範例會使用`Select`中的子句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select` C# 中的子句) 和*匿名型別*傳回*形狀子集*客戶相關的資料。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-121">The following example uses a `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="ee6d9-122">範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-122">Example</span></span>  
 <span data-ttu-id="ee6d9-123">下列範例使用巢狀查詢，傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="ee6d9-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="ee6d9-124">所有訂單與其對應 `OrderID` 的序列。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="ee6d9-125">訂單中有折扣之項目的序列。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="ee6d9-126">不包含運送成本時所節省的金額。</span><span class="sxs-lookup"><span data-stu-id="ee6d9-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="ee6d9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee6d9-127">See Also</span></span>  
 [<span data-ttu-id="ee6d9-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="ee6d9-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
