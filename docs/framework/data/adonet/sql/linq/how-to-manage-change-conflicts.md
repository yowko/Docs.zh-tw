---
title: 作法：管理變更衝突
ms.date: 03/30/2017
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
ms.openlocfilehash: 496971a99522c2547759905833ce2e89ea00826b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173402"
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="5ffa4-102">作法：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="5ffa4-102">How to: Manage Change Conflicts</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5ffa4-103">提供 Api 集合，可協助您探索、評估和解決並行衝突。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-103">provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ffa4-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="5ffa4-104">In This Section</span></span>  

 [<span data-ttu-id="5ffa4-105">作法：偵測和解決發生衝突的提交內容</span><span class="sxs-lookup"><span data-stu-id="5ffa4-105">How to: Detect and Resolve Conflicting Submissions</span></span>](how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="5ffa4-106">描述如何偵測和解決並行存取衝突。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="5ffa4-107">作法：指定並行例外狀況的擲回時機</span><span class="sxs-lookup"><span data-stu-id="5ffa4-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="5ffa4-108">描述如何指定應該通知您發生並行存取衝突的時機。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="5ffa4-109">作法：指定用於測試並行衝突的成員</span><span class="sxs-lookup"><span data-stu-id="5ffa4-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="5ffa4-110">描述如何將成員加上屬性 (Attribute)，以指定是否要檢查這些屬性是否發生並行存取衝突。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="5ffa4-111">作法：擷取實體衝突資訊</span><span class="sxs-lookup"><span data-stu-id="5ffa4-111">How to: Retrieve Entity Conflict Information</span></span>](how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="5ffa4-112">描述如何蒐集實體衝突的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="5ffa4-113">作法：擷取成員衝突資訊</span><span class="sxs-lookup"><span data-stu-id="5ffa4-113">How to: Retrieve Member Conflict Information</span></span>](how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="5ffa4-114">描述如何蒐集成員衝突的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="5ffa4-115">作法：藉由保留資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="5ffa4-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="5ffa4-116">描述如何以資料庫值覆寫目前值。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="5ffa4-117">作法：藉由覆寫資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="5ffa4-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="5ffa4-118">描述如何覆寫資料庫值來保留目前值。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="5ffa4-119">作法：藉由與資料庫值合併來解決衝突</span><span class="sxs-lookup"><span data-stu-id="5ffa4-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="5ffa4-120">描述如何合併資料庫和目前值來解決衝突。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ffa4-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="5ffa4-121">Related Sections</span></span>  

 [<span data-ttu-id="5ffa4-122">開放式並行存取：總覽</span><span class="sxs-lookup"><span data-stu-id="5ffa4-122">Optimistic Concurrency: Overview</span></span>](optimistic-concurrency-overview.md)  
 <span data-ttu-id="5ffa4-123">說明適用於 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中開放式並行存取 (Optimistic Concurrency) 的詞彙。</span><span class="sxs-lookup"><span data-stu-id="5ffa4-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
