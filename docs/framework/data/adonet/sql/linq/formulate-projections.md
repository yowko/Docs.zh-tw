---
title: 制定投影
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: d8215a016face76b8a258d694a36657be327b5e0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="formulate-projections"></a><span data-ttu-id="1bbf2-102">制定投影</span><span class="sxs-lookup"><span data-stu-id="1bbf2-102">Formulate Projections</span></span>
<span data-ttu-id="1bbf2-103">下列範例會顯示如何`select`C# 中的陳述式和`Select`在 Visual Basic 中的陳述式可以結合其他功能，以構成查詢投影。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bbf2-104">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-104">Example</span></span>  
 <span data-ttu-id="1bbf2-105">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 以傳回的連絡人名稱序列`Customers`。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="1bbf2-106">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-106">Example</span></span>  
 <span data-ttu-id="1bbf2-107">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*匿名型別*要傳回的連絡人名稱序列和電話號碼`Customers`。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="1bbf2-108">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-108">Example</span></span>  
 <span data-ttu-id="1bbf2-109">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*匿名型別*傳回一連串的名稱，並為員工電話號碼。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="1bbf2-110">`FirstName`和`LastName`欄位會合併成單一欄位 (`Name`)，而`HomePhone`欄位重新命名為`Phone`中所產生的順序。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="1bbf2-111">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-111">Example</span></span>  
 <span data-ttu-id="1bbf2-112">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*匿名型別*以傳回所有序列`ProductID`s 和名為的導出的值`HalfPrice`。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="1bbf2-113">此值設為 `UnitPrice` 除以 2。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="1bbf2-114">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-114">Example</span></span>  
 <span data-ttu-id="1bbf2-115">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*條件陳述式*傳回一連串的產品名稱和產品可用性。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="1bbf2-116">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-116">Example</span></span>  
 <span data-ttu-id="1bbf2-117">下列範例會使用 Visual Basic`Select`子句 (`select`子句在 C# 中的) 和*已知型別*(Name)，傳回員工的名稱的序列。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="1bbf2-118">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-118">Example</span></span>  
 <span data-ttu-id="1bbf2-119">下列範例會使用`Select`和`Where`在 Visual Basic 中 (`select`和`where`C# 中) 來傳回*篩選順序*位於倫敦的客戶的連絡人名稱。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="1bbf2-120">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-120">Example</span></span>  
 <span data-ttu-id="1bbf2-121">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*匿名型別*傳回*形狀子集*客戶相關的資料。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="1bbf2-122">範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-122">Example</span></span>  
 <span data-ttu-id="1bbf2-123">下列範例使用巢狀查詢，傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="1bbf2-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="1bbf2-124">所有訂單與其對應 `OrderID` 的序列。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="1bbf2-125">訂單中有折扣之項目的序列。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="1bbf2-126">不包含運送成本時所節省的金額。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="1bbf2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bbf2-127">See Also</span></span>  
 [<span data-ttu-id="1bbf2-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="1bbf2-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
