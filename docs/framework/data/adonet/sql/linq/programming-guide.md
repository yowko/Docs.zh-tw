---
title: "程式設計手冊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03d4febc7e61425d0057c48949b18281ca3dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="programming-guide"></a><span data-ttu-id="3fdaa-102">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="3fdaa-102">Programming Guide</span></span>
<span data-ttu-id="3fdaa-103">本節包含如何建立和使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型 (Object Model) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="3fdaa-104">如果您使用的是 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]，也可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來執行許多相同的工作。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-104">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="3fdaa-105">您也可以搜尋特定問題，Microsoft 文件，而且可以參與[LINQ 論壇](http://go.microsoft.com/fwlink/?LinkId=76488)，您可以在其中討論與專家更複雜的主題的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="3fdaa-106">最後，[LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) (LINQ to SQL：關聯式資料的 .NET Language-Integrated Query) 白皮書會詳述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術，其中包含 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 和 C# 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3fdaa-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="3fdaa-107">In This Section</span></span>  
 [<span data-ttu-id="3fdaa-108">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="3fdaa-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="3fdaa-109">描述如何產生物件模型。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="3fdaa-110">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="3fdaa-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="3fdaa-111">描述如何使用 <xref:System.Data.Linq.DataContext> 物件做為連接資料庫的管道。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="3fdaa-112">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="3fdaa-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="3fdaa-113">描述如何在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中執行查詢，以及提供許多範例。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="3fdaa-114">建立和提交資料變更</span><span class="sxs-lookup"><span data-stu-id="3fdaa-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="3fdaa-115">描述如何變更資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="3fdaa-116">偵錯支援</span><span class="sxs-lookup"><span data-stu-id="3fdaa-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="3fdaa-117">描述可用來偵錯 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案的支援。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="3fdaa-118">背景資訊</span><span class="sxs-lookup"><span data-stu-id="3fdaa-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="3fdaa-119">包括更進階使用者適用的額外項目，例如並行存取衝突解決、建立新資料庫等。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3fdaa-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="3fdaa-120">Related Sections</span></span>  
 [<span data-ttu-id="3fdaa-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3fdaa-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="3fdaa-122">提供說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術以及示範功能的主題連結。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="3fdaa-123">預存程序</span><span class="sxs-lookup"><span data-stu-id="3fdaa-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="3fdaa-124">包括說明如何使用預存程序 (Stored Procedure) 的主題連結。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="3fdaa-125">LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="3fdaa-125">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 <span data-ttu-id="3fdaa-126">提供協助您開始學習 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的資源。</span><span class="sxs-lookup"><span data-stu-id="3fdaa-126">Provides resources to help you begin to learn about [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
