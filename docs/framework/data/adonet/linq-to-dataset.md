---
title: LINQ to DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 75ab1e733915349c64742e1a9c1142cad988ade0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-dataset"></a><span data-ttu-id="1d219-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1d219-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="1d219-103"> 可讓您更方便且更快速地查詢在 <xref:System.Data.DataSet> 物件中快取的資料。</span><span class="sxs-lookup"><span data-stu-id="1d219-103"> makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="1d219-104">具體來說，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]簡化查詢，讓開發人員從程式語言本身撰寫查詢而不是使用不同的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="1d219-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="1d219-105">這是特別適用於[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]開發人員現在能夠利用編譯時期語法檢查、 靜態型別和 IntelliSense 支援所提供的優點[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]在查詢中。</span><span class="sxs-lookup"><span data-stu-id="1d219-105">This is especially useful for [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="1d219-106"> 也可用來查詢已經從一個或多個資料來源合併的資料。</span><span class="sxs-lookup"><span data-stu-id="1d219-106"> can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="1d219-107">這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。</span><span class="sxs-lookup"><span data-stu-id="1d219-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="1d219-108">尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。</span><span class="sxs-lookup"><span data-stu-id="1d219-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="1d219-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]功能中的擴充方法主要是透過公開<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別。</span><span class="sxs-lookup"><span data-stu-id="1d219-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="1d219-110">為基礎，並使用現有[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]架構，而不是取代[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]應用程式程式碼中。</span><span class="sxs-lookup"><span data-stu-id="1d219-110"> builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="1d219-111">現有的 ADO.NET 2.0 程式碼將繼續在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="1d219-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="1d219-112">下圖將說明 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 與 [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] 的關聯性以及資料存放區。</span><span class="sxs-lookup"><span data-stu-id="1d219-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 <span data-ttu-id="1d219-113">![LINQ to DataSet 根據 ADO.NET 提供者](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span><span class="sxs-lookup"><span data-stu-id="1d219-113">![LINQ to DataSet is based on the ADO.NET Provider](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d219-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="1d219-114">In This Section</span></span>  
 [<span data-ttu-id="1d219-115">快速入門</span><span class="sxs-lookup"><span data-stu-id="1d219-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="1d219-116">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="1d219-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="1d219-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="1d219-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="1d219-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d219-118">See Also</span></span>  
 [<span data-ttu-id="1d219-119">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="1d219-119">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="1d219-120">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1d219-120">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [<span data-ttu-id="1d219-121">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1d219-121">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
