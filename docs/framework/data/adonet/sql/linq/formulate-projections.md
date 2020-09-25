---
title: 制定投影
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f0bc6dfcff7778ebc7156cbb039e13570c90467b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194397"
---
# <a name="formulate-projections"></a><span data-ttu-id="b1d6a-102">制定投影</span><span class="sxs-lookup"><span data-stu-id="b1d6a-102">Formulate Projections</span></span>

<span data-ttu-id="b1d6a-103">下列範例示範 `select` c # 中的語句和 `Select` Visual Basic 中的語句如何與其他功能結合，以構成查詢投影。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1d6a-104">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-104">Example</span></span>  

 <span data-ttu-id="b1d6a-105">下列範例會在 `Select` c # ) 的 Visual Basic (子句中使用子句 `select` ，以傳回的連絡人名稱序列 `Customers` 。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="b1d6a-106">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-106">Example</span></span>  

 <span data-ttu-id="b1d6a-107">下列範例會在 `Select` c # 中使用 Visual Basic (子句中的子句 `select` ) 和 *匿名型別* 會傳回的連絡人名稱和電話號碼序列 `Customers` 。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="b1d6a-108">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-108">Example</span></span>  

 <span data-ttu-id="b1d6a-109">下列範例會在 `Select` c # 中使用 Visual Basic (子句中的子句 `select` ) 和 *匿名* 型別，以傳回員工的名稱和電話號碼序列。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="b1d6a-110">`FirstName`和 `LastName` 欄位會合並成單一欄位 (`Name`) ，而且 `HomePhone` 欄位會 `Phone` 在產生的序列中重新命名為。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="b1d6a-111">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-111">Example</span></span>  

 <span data-ttu-id="b1d6a-112">下列範例會在 `Select` c # 中使用 Visual Basic (子句中的子句 `select` ) 和 *匿名* 型別會傳回所有 s 的序列 `ProductID` 和名為的計算值 `HalfPrice` 。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="b1d6a-113">此值設為 `UnitPrice` 除以 2。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="b1d6a-114">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-114">Example</span></span>  

 <span data-ttu-id="b1d6a-115">下列範例會在 `Select` c # ) 中使用 Visual Basic (子句中的子句 `select` ，並使用 *條件陳述式* 來傳回產品名稱和產品可用性的序列。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="b1d6a-116">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-116">Example</span></span>  

 <span data-ttu-id="b1d6a-117">下列範例會 `Select` `select` 在 c # 中使用 Visual Basic 子句 (子句 ) 以及 *已知的類型* (名稱) ，以傳回員工名稱的序列。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="b1d6a-118">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-118">Example</span></span>  

 <span data-ttu-id="b1d6a-119">下列範例會在 `Select` `Where` Visual Basic (`select` 和 `where` c # ) 中使用和，以針對位於倫敦的客戶傳回已篩選的連絡人名稱 *序列* 。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="b1d6a-120">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-120">Example</span></span>  

 <span data-ttu-id="b1d6a-121">下列範例會在 `Select` c # 中使用 Visual Basic (子句中的子句 `select` ) 和 *匿名* 型別，以傳回客戶相關資料的 *成形子集* 。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="b1d6a-122">範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-122">Example</span></span>  

 <span data-ttu-id="b1d6a-123">下列範例使用巢狀查詢，傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="b1d6a-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="b1d6a-124">所有訂單與其對應 `OrderID` 的序列。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="b1d6a-125">訂單中有折扣之項目的序列。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="b1d6a-126">不包含運送成本時所節省的金額。</span><span class="sxs-lookup"><span data-stu-id="b1d6a-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="b1d6a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1d6a-127">See also</span></span>

- [<span data-ttu-id="b1d6a-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="b1d6a-128">Query Examples</span></span>](query-examples.md)
