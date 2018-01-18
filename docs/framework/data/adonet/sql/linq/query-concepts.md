---
title: "查詢概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a125749-ccb5-49d5-999d-d2db7171d74d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4bea41ad092de4afe1a2fff7927321d63c43278e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="query-concepts"></a><span data-ttu-id="70a7c-102">查詢概念</span><span class="sxs-lookup"><span data-stu-id="70a7c-102">Query Concepts</span></span>
<span data-ttu-id="70a7c-103">本節說明在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中設計 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的主要概念。</span><span class="sxs-lookup"><span data-stu-id="70a7c-103">This section describes key concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70a7c-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="70a7c-104">In This Section</span></span>  
 [<span data-ttu-id="70a7c-105">LINQ to SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="70a7c-105">LINQ to SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-queries.md)  
 <span data-ttu-id="70a7c-106">參考 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 一般主題，並說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 特有的項目。</span><span class="sxs-lookup"><span data-stu-id="70a7c-106">Refers to general [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] topics, and explains items specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="70a7c-107">跨關聯性查詢</span><span class="sxs-lookup"><span data-stu-id="70a7c-107">Querying Across Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)  
 <span data-ttu-id="70a7c-108">說明如何使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型中的關聯。</span><span class="sxs-lookup"><span data-stu-id="70a7c-108">Explains how to use associations in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="70a7c-109">遠端與本機執行的比較</span><span class="sxs-lookup"><span data-stu-id="70a7c-109">Remote vs. Local Execution</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)  
 <span data-ttu-id="70a7c-110">說明如何指定您要執行查詢的位置。</span><span class="sxs-lookup"><span data-stu-id="70a7c-110">Explains how to specify where you want your query executed.</span></span>  
  
 [<span data-ttu-id="70a7c-111">延後與立即載入的比較</span><span class="sxs-lookup"><span data-stu-id="70a7c-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)  
 <span data-ttu-id="70a7c-112">說明如何指定載入相關物件的時間。</span><span class="sxs-lookup"><span data-stu-id="70a7c-112">Describes how to specify when related objects are loaded.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70a7c-113">相關章節</span><span class="sxs-lookup"><span data-stu-id="70a7c-113">Related Sections</span></span>  
 [<span data-ttu-id="70a7c-114">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="70a7c-114">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="70a7c-115">包含可說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術的主題連結。</span><span class="sxs-lookup"><span data-stu-id="70a7c-115">Contains links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology.</span></span>  
  
 [<span data-ttu-id="70a7c-116">物件身分識別</span><span class="sxs-lookup"><span data-stu-id="70a7c-116">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 <span data-ttu-id="70a7c-117">說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的物件識別概念。</span><span class="sxs-lookup"><span data-stu-id="70a7c-117">Explains the concept of object identity in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="70a7c-118">LINQ 查詢簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="70a7c-118">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="70a7c-119">提供 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中查詢作業的簡介。</span><span class="sxs-lookup"><span data-stu-id="70a7c-119">Provides an introduction to query operations in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
