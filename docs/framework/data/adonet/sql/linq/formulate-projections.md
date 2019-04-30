---
title: 制定投影
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: e1f7a7da1ab2ce0ad7d7908ecd1f896d229b8e1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037904"
---
# <a name="formulate-projections"></a><span data-ttu-id="dba29-102">制定投影</span><span class="sxs-lookup"><span data-stu-id="dba29-102">Formulate Projections</span></span>
<span data-ttu-id="dba29-103">下列範例會顯示如何`select`中的陳述式C#並`Select`在 Visual Basic 中的陳述式可以結合其他功能，以構成查詢投影。</span><span class="sxs-lookup"><span data-stu-id="dba29-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dba29-104">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-104">Example</span></span>  
 <span data-ttu-id="dba29-105">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句C#) 以傳回的連絡人名稱序列`Customers`。</span><span class="sxs-lookup"><span data-stu-id="dba29-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="dba29-106">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-106">Example</span></span>  
 <span data-ttu-id="dba29-107">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句C#) 和*匿名型別*要傳回一連串的連絡人名稱和電話號碼`Customers`。</span><span class="sxs-lookup"><span data-stu-id="dba29-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="dba29-108">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-108">Example</span></span>  
 <span data-ttu-id="dba29-109">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句C#) 和*匿名型別*傳回一連串的名稱和電話號碼的員工。</span><span class="sxs-lookup"><span data-stu-id="dba29-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="dba29-110">`FirstName`並`LastName`欄位會合併成單一欄位 (`Name`)，而`HomePhone`欄位已重新命名為`Phone`中產生的序列。</span><span class="sxs-lookup"><span data-stu-id="dba29-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="dba29-111">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-111">Example</span></span>  
 <span data-ttu-id="dba29-112">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句C#) 和*匿名型別*要傳回的一系列所有`ProductID`s 和名為的導出的值`HalfPrice`。</span><span class="sxs-lookup"><span data-stu-id="dba29-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="dba29-113">此值設為 `UnitPrice` 除以 2。</span><span class="sxs-lookup"><span data-stu-id="dba29-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="dba29-114">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-114">Example</span></span>  
 <span data-ttu-id="dba29-115">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句C#) 和*條件陳述式*要傳回的產品名稱和產品可用性的序列。</span><span class="sxs-lookup"><span data-stu-id="dba29-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="dba29-116">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-116">Example</span></span>  
 <span data-ttu-id="dba29-117">下列範例會使用 Visual Basic`Select`子句 (`select`子句C#) 和*已知型別*(Name)，傳回一連串的員工的名稱。</span><span class="sxs-lookup"><span data-stu-id="dba29-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="dba29-118">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-118">Example</span></span>  
 <span data-ttu-id="dba29-119">下列範例會使用`Select`和`Where`Visual Basic 中 (`select`並`where`中C#) 傳回*篩選序列*位於倫敦的客戶連絡人的名稱。</span><span class="sxs-lookup"><span data-stu-id="dba29-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="dba29-120">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-120">Example</span></span>  
 <span data-ttu-id="dba29-121">下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句C#) 和*匿名型別*返回*形狀子集*的客戶相關資料。</span><span class="sxs-lookup"><span data-stu-id="dba29-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="dba29-122">範例</span><span class="sxs-lookup"><span data-stu-id="dba29-122">Example</span></span>  
 <span data-ttu-id="dba29-123">下列範例使用巢狀查詢，傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="dba29-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="dba29-124">所有訂單與其對應 `OrderID` 的序列。</span><span class="sxs-lookup"><span data-stu-id="dba29-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="dba29-125">訂單中有折扣之項目的序列。</span><span class="sxs-lookup"><span data-stu-id="dba29-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="dba29-126">不包含運送成本時所節省的金額。</span><span class="sxs-lookup"><span data-stu-id="dba29-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="dba29-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba29-127">See also</span></span>

- [<span data-ttu-id="dba29-128">查詢範例</span><span class="sxs-lookup"><span data-stu-id="dba29-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
