---
title: 使用部分方法加入商務邏輯
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
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 8ea345f01c68f8c962069a3e9fdca7feff84c5c0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="b7599-102">使用部分方法加入商務邏輯</span><span class="sxs-lookup"><span data-stu-id="b7599-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="b7599-103">您可以自訂 Visual Basic 和 C# 產生程式碼中的您[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]使用專案*部分方法*。</span><span class="sxs-lookup"><span data-stu-id="b7599-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="b7599-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 產生的程式碼會將簽章定義成部分方法的一部分。</span><span class="sxs-lookup"><span data-stu-id="b7599-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="b7599-105">如果您想實作此方法，可以加入自己的部分方法。</span><span class="sxs-lookup"><span data-stu-id="b7599-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="b7599-106">如果您未加入自己的實作 (Implementation)，則編譯器 (Compiler) 會捨棄部分方法簽章並呼叫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的預設方法。</span><span class="sxs-lookup"><span data-stu-id="b7599-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7599-107">如果您使用 Visual Studio，您可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]將驗證和其他自訂加入至實體類別。</span><span class="sxs-lookup"><span data-stu-id="b7599-107">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="b7599-108">例如，Northwind 範例資料庫中 `Customer` 類別的預設對應包含下列部分方法：</span><span class="sxs-lookup"><span data-stu-id="b7599-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="b7599-109">您可以將下列程式碼加入至自己的部分 `Customer` 類別，進而實作自己的方法：</span><span class="sxs-lookup"><span data-stu-id="b7599-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="b7599-110">這種方法通常用於[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]覆寫預設方法，如`Insert`， `Update`， `Delete`，並驗證物件生命週期事件期間的屬性。</span><span class="sxs-lookup"><span data-stu-id="b7599-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="b7599-111">如需詳細資訊，請參閱[部分方法](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)(Visual Basic) 或[partial （方法） （C# 參考）](~/docs/csharp/language-reference/keywords/partial-method.md) (C#)。</span><span class="sxs-lookup"><span data-stu-id="b7599-111">For more information, see [Partial Methods](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7599-112">範例</span><span class="sxs-lookup"><span data-stu-id="b7599-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b7599-113">描述</span><span class="sxs-lookup"><span data-stu-id="b7599-113">Description</span></span>  
 <span data-ttu-id="b7599-114">下列範例會先顯示 `ExampleClass`，因為它可能是由程式碼產生工具 (例如 SQLMetal) 所定義，然後顯示您如何僅實作其中一種方法。</span><span class="sxs-lookup"><span data-stu-id="b7599-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b7599-115">程式碼</span><span class="sxs-lookup"><span data-stu-id="b7599-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="b7599-116">範例</span><span class="sxs-lookup"><span data-stu-id="b7599-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b7599-117">描述</span><span class="sxs-lookup"><span data-stu-id="b7599-117">Description</span></span>  
 <span data-ttu-id="b7599-118">下列範例會使用 `Shipper` 和 `Order` 實體 (Entity) 之間的關聯性 (Relationship)。</span><span class="sxs-lookup"><span data-stu-id="b7599-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="b7599-119">請注意部分方法中的 `InsertShipper` 和 `DeleteShipper` 方法。</span><span class="sxs-lookup"><span data-stu-id="b7599-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="b7599-120">這些方法會覆寫所提供的預設部分方法[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]對應。</span><span class="sxs-lookup"><span data-stu-id="b7599-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b7599-121">程式碼</span><span class="sxs-lookup"><span data-stu-id="b7599-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b7599-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7599-122">See Also</span></span>  
 [<span data-ttu-id="b7599-123">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="b7599-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="b7599-124">自訂插入、更新和刪除作業</span><span class="sxs-lookup"><span data-stu-id="b7599-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
