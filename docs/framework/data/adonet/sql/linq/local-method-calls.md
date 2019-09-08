---
title: 區域方法呼叫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: ec288d5ac2f6466860362be82c619c89204e8f31
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781415"
---
# <a name="local-method-calls"></a><span data-ttu-id="d60a7-102">區域方法呼叫</span><span class="sxs-lookup"><span data-stu-id="d60a7-102">Local Method Calls</span></span>
<span data-ttu-id="d60a7-103">區域方法呼叫就是在物件模型 (Object Model) 內執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d60a7-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="d60a7-104">遠端方法呼叫則是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 轉譯為 SQL 並傳輸給資料庫引擎進行執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d60a7-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="d60a7-105">當無法將呼叫轉譯為[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 時，需要區域方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="d60a7-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="d60a7-106">否則會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="d60a7-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="d60a7-107">範例 1</span><span class="sxs-lookup"><span data-stu-id="d60a7-107">Example 1</span></span>  
 <span data-ttu-id="d60a7-108">在下列範例中，`Order` 類別會對應至 Northwind 範例資料庫中的 Orders 資料表。</span><span class="sxs-lookup"><span data-stu-id="d60a7-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="d60a7-109">本機執行個體方法已加入至這個類別中。</span><span class="sxs-lookup"><span data-stu-id="d60a7-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="d60a7-110">在查詢 1 中，會在本機執行 `Order` 類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="d60a7-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="d60a7-111">在查詢 2 中，如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 嘗試將 `LocalInstanceMethod()` 轉譯為 SQL，則嘗試會失敗，而且會擲回 <xref:System.InvalidOperationException> 例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="d60a7-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="d60a7-112">但是因為 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援區域方法呼叫，所以查詢 2 不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d60a7-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d60a7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d60a7-113">See also</span></span>

- [<span data-ttu-id="d60a7-114">背景資訊</span><span class="sxs-lookup"><span data-stu-id="d60a7-114">Background Information</span></span>](background-information.md)
