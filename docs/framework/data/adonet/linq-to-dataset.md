---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 5e1644af7e07ad3395a30e56df52b7f85cefa77c
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006086"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="b55f9-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="b55f9-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="b55f9-103"> 可讓您更方便且更快速地查詢在 <xref:System.Data.DataSet> 物件中快取的資料。</span><span class="sxs-lookup"><span data-stu-id="b55f9-103"> makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="b55f9-104">具體來說，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]簡化查詢，讓開發人員撰寫查詢，從程式語言本身，而不是使用不同的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="b55f9-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="b55f9-105">這是特別適用於 Visual Studio 開發人員來說，現在可以利用的編譯時間語法檢查、 靜態型別和 Visual Studio，在查詢中所提供的 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="b55f9-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="b55f9-106"> 也可用來查詢已經從一個或多個資料來源合併的資料。</span><span class="sxs-lookup"><span data-stu-id="b55f9-106"> can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="b55f9-107">這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。</span><span class="sxs-lookup"><span data-stu-id="b55f9-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="b55f9-108">尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。</span><span class="sxs-lookup"><span data-stu-id="b55f9-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="b55f9-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]功能會公開主要是透過的擴充方法<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別。</span><span class="sxs-lookup"><span data-stu-id="b55f9-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="b55f9-110"> 建置基礎，並使用現有[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]架構，而不是取代[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]應用程式程式碼中。</span><span class="sxs-lookup"><span data-stu-id="b55f9-110"> builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="b55f9-111">現有的 ADO.NET 2.0 程式碼將繼續在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="b55f9-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="b55f9-112">下圖將說明 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 與 [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] 的關聯性以及資料存放區。</span><span class="sxs-lookup"><span data-stu-id="b55f9-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 <span data-ttu-id="b55f9-113">![LINQ to DataSet 以 ADO.NET 提供者為基礎](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span><span class="sxs-lookup"><span data-stu-id="b55f9-113">![LINQ to DataSet is based on the ADO.NET Provider](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b55f9-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="b55f9-114">In This Section</span></span>  
 [<span data-ttu-id="b55f9-115">快速入門</span><span class="sxs-lookup"><span data-stu-id="b55f9-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="b55f9-116">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="b55f9-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="b55f9-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="b55f9-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="b55f9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b55f9-118">See Also</span></span>  
 [<span data-ttu-id="b55f9-119">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="b55f9-119">LINQ (Language-Integrated Query)</span></span>](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="b55f9-120">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b55f9-120">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [<span data-ttu-id="b55f9-121">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b55f9-121">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
