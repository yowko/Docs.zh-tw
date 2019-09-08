---
title: 作法：管理變更衝突
ms.date: 03/30/2017
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
ms.openlocfilehash: 49ccb08a375b612e62a8911e98f8ec08058802db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781831"
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="75b0c-102">HOW TO：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="75b0c-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="75b0c-103">提供 Api 的集合，可協助您探索、評估和解決並行衝突。</span><span class="sxs-lookup"><span data-stu-id="75b0c-103">provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75b0c-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="75b0c-104">In This Section</span></span>  
 [<span data-ttu-id="75b0c-105">如何：偵測並解決衝突的提交</span><span class="sxs-lookup"><span data-stu-id="75b0c-105">How to: Detect and Resolve Conflicting Submissions</span></span>](how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="75b0c-106">描述如何偵測和解決並行存取衝突。</span><span class="sxs-lookup"><span data-stu-id="75b0c-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="75b0c-107">如何：指定並行例外狀況的擲回時機</span><span class="sxs-lookup"><span data-stu-id="75b0c-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="75b0c-108">描述如何指定應該通知您發生並行存取衝突的時機。</span><span class="sxs-lookup"><span data-stu-id="75b0c-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="75b0c-109">如何：指定測試並行衝突的成員</span><span class="sxs-lookup"><span data-stu-id="75b0c-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="75b0c-110">描述如何將成員加上屬性 (Attribute)，以指定是否要檢查這些屬性是否發生並行存取衝突。</span><span class="sxs-lookup"><span data-stu-id="75b0c-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="75b0c-111">如何：取得實體衝突資訊</span><span class="sxs-lookup"><span data-stu-id="75b0c-111">How to: Retrieve Entity Conflict Information</span></span>](how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="75b0c-112">描述如何蒐集實體衝突的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="75b0c-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="75b0c-113">如何：取得成員衝突資訊</span><span class="sxs-lookup"><span data-stu-id="75b0c-113">How to: Retrieve Member Conflict Information</span></span>](how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="75b0c-114">描述如何蒐集成員衝突的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="75b0c-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="75b0c-115">如何：藉由保留資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="75b0c-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="75b0c-116">描述如何以資料庫值覆寫目前值。</span><span class="sxs-lookup"><span data-stu-id="75b0c-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="75b0c-117">如何：藉由覆寫資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="75b0c-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="75b0c-118">描述如何覆寫資料庫值來保留目前值。</span><span class="sxs-lookup"><span data-stu-id="75b0c-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="75b0c-119">如何：藉由與資料庫值合併來解決衝突</span><span class="sxs-lookup"><span data-stu-id="75b0c-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="75b0c-120">描述如何合併資料庫和目前值來解決衝突。</span><span class="sxs-lookup"><span data-stu-id="75b0c-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="75b0c-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="75b0c-121">Related Sections</span></span>  
 [<span data-ttu-id="75b0c-122">開放式平行存取：概觀</span><span class="sxs-lookup"><span data-stu-id="75b0c-122">Optimistic Concurrency: Overview</span></span>](optimistic-concurrency-overview.md)  
 <span data-ttu-id="75b0c-123">說明適用於 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中開放式並行存取 (Optimistic Concurrency) 的詞彙。</span><span class="sxs-lookup"><span data-stu-id="75b0c-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
