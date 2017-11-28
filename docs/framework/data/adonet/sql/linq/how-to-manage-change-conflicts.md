---
title: "如何：管理變更衝突"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 87d895c8d5531d091d773e9f2d51b89408169022
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="293cc-102">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="293cc-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="293cc-103">提供 Api，可協助您探索、 評估並解決並行衝突的集合。</span><span class="sxs-lookup"><span data-stu-id="293cc-103"> provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="293cc-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="293cc-104">In This Section</span></span>  
 [<span data-ttu-id="293cc-105">如何： 偵測及解決衝突的提交</span><span class="sxs-lookup"><span data-stu-id="293cc-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="293cc-106">描述如何偵測和解決並行存取衝突。</span><span class="sxs-lookup"><span data-stu-id="293cc-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="293cc-107">如何： 指定並行例外狀況會擲回</span><span class="sxs-lookup"><span data-stu-id="293cc-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="293cc-108">描述如何指定應該通知您發生並行存取衝突的時機。</span><span class="sxs-lookup"><span data-stu-id="293cc-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="293cc-109">如何： 指定的成員會用於測試並行衝突</span><span class="sxs-lookup"><span data-stu-id="293cc-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="293cc-110">描述如何將成員加上屬性 (Attribute)，以指定是否要檢查這些屬性是否發生並行存取衝突。</span><span class="sxs-lookup"><span data-stu-id="293cc-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="293cc-111">如何： 擷取實體衝突資訊</span><span class="sxs-lookup"><span data-stu-id="293cc-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="293cc-112">描述如何蒐集實體衝突的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="293cc-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="293cc-113">如何： 擷取成員衝突資訊</span><span class="sxs-lookup"><span data-stu-id="293cc-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="293cc-114">描述如何蒐集成員衝突的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="293cc-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="293cc-115">如何： 解決衝突，藉由保留資料庫值</span><span class="sxs-lookup"><span data-stu-id="293cc-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="293cc-116">描述如何以資料庫值覆寫目前值。</span><span class="sxs-lookup"><span data-stu-id="293cc-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="293cc-117">如何： 覆寫資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="293cc-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="293cc-118">描述如何覆寫資料庫值來保留目前值。</span><span class="sxs-lookup"><span data-stu-id="293cc-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="293cc-119">如何： 藉由合併資料庫值來解決衝突</span><span class="sxs-lookup"><span data-stu-id="293cc-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="293cc-120">描述如何合併資料庫和目前值來解決衝突。</span><span class="sxs-lookup"><span data-stu-id="293cc-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="293cc-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="293cc-121">Related Sections</span></span>  
 [<span data-ttu-id="293cc-122">開放式並行存取： 概觀</span><span class="sxs-lookup"><span data-stu-id="293cc-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="293cc-123">說明適用於 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中開放式並行存取 (Optimistic Concurrency) 的詞彙。</span><span class="sxs-lookup"><span data-stu-id="293cc-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
