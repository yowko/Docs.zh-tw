---
title: 制定投影
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793825"
---
# <a name="formulate-projections"></a><span data-ttu-id="f5cfd-102">制定投影</span><span class="sxs-lookup"><span data-stu-id="f5cfd-102">Formulate Projections</span></span>
<span data-ttu-id="f5cfd-103">下列範例會示範如何將`select` Visual Basic 中C#的`Select`語句與其他功能結合，以形成查詢投影。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5cfd-104">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-104">Example</span></span>  
 <span data-ttu-id="f5cfd-105">下列範例會在中`Select` C#使用 Visual Basic （ `Customers` `select`子句）中的子句，以傳回的連絡人名稱序列。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="f5cfd-106">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-106">Example</span></span>  
 <span data-ttu-id="f5cfd-107">下列範例會在的`Select` Visual Basic （`select`子句C#）和*匿名*型別中使用子句，以傳回的連絡人名稱和電話號碼`Customers`序列。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="f5cfd-108">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-108">Example</span></span>  
 <span data-ttu-id="f5cfd-109">下列範例會在的`Select` Visual Basic （`select`子句C#）和*匿名型別*中使用子句，以傳回員工的名稱和電話號碼序列。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="f5cfd-110">`Phone` `HomePhone` `Name`和欄位會合並成單一欄位（），而欄位會在產生的序列中重新命名為。 `LastName` `FirstName`</span><span class="sxs-lookup"><span data-stu-id="f5cfd-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="f5cfd-111">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-111">Example</span></span>  
 <span data-ttu-id="f5cfd-112">下列範例會在的`Select` Visual Basic （`select`子句C#）和*匿名*型別中使用子句，以傳回所有`ProductID`的序列和名為`HalfPrice`的計算值。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="f5cfd-113">此值設為 `UnitPrice` 除以 2。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="f5cfd-114">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-114">Example</span></span>  
 <span data-ttu-id="f5cfd-115">下列範例會在的`Select` Visual Basic （`select`子句C#）和*條件陳述式*中使用子句，以傳回產品名稱和產品可用性的序列。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="f5cfd-116">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-116">Example</span></span>  
 <span data-ttu-id="f5cfd-117">下列範例`Select`會使用 Visual Basic 子句（`select`中C#的子句）和*已知型*別（名稱）來傳回員工名稱的序列。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="f5cfd-118">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-118">Example</span></span>  
 <span data-ttu-id="f5cfd-119">下列範例會在`Select` Visual Basic `Where`中使用和`select` （ `where`在C#中為），以針對倫敦的客戶傳回已篩選的連絡人名稱*序列*。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="f5cfd-120">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-120">Example</span></span>  
 <span data-ttu-id="f5cfd-121">下列範例會在的`Select` Visual Basic （`select`子句C#）和*匿名*型別中使用子句，以傳回有關客戶資料的*形狀子集*。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="f5cfd-122">範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-122">Example</span></span>  
 <span data-ttu-id="f5cfd-123">下列範例使用巢狀查詢，傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="f5cfd-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="f5cfd-124">所有訂單與其對應 `OrderID` 的序列。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="f5cfd-125">訂單中有折扣之項目的序列。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="f5cfd-126">不包含運送成本時所節省的金額。</span><span class="sxs-lookup"><span data-stu-id="f5cfd-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="f5cfd-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5cfd-127">See also</span></span>

- [<span data-ttu-id="f5cfd-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="f5cfd-128">Query Examples</span></span>](query-examples.md)
