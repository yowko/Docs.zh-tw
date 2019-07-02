---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504362"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="f7919-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f7919-102">LINQ to DataSet</span></span>
<span data-ttu-id="f7919-103">LINQ to DataSet 可輕鬆並更快速地對資料的查詢快取在<xref:System.Data.DataSet>物件。</span><span class="sxs-lookup"><span data-stu-id="f7919-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="f7919-104">具體而言，LINQ to DataSet 可簡化讓開發人員撰寫查詢，從程式語言本身，而不是使用不同的查詢語言查詢。</span><span class="sxs-lookup"><span data-stu-id="f7919-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="f7919-105">這是特別適用於 Visual Studio 開發人員來說，現在可以利用的編譯時間語法檢查、 靜態型別和 Visual Studio，在查詢中所提供的 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="f7919-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="f7919-106">也可以用 LINQ to DataSet 查詢已合併一或多個資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="f7919-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="f7919-107">這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。</span><span class="sxs-lookup"><span data-stu-id="f7919-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="f7919-108">尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。</span><span class="sxs-lookup"><span data-stu-id="f7919-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="f7919-109">LINQ to DataSet 功能會公開主要是透過的擴充方法<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別。</span><span class="sxs-lookup"><span data-stu-id="f7919-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="f7919-110">LINQ to DataSet 是根據和使用現有的 ADO.NET 架構，而不是取代應用程式程式碼中的 ADO.NET。</span><span class="sxs-lookup"><span data-stu-id="f7919-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="f7919-111">現有的 ADO.NET 程式碼會繼續在 LINQ to DataSet 應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="f7919-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="f7919-112">LINQ to ADO.NET 和資料存放區的資料集的關聯性是由下列圖所示。</span><span class="sxs-lookup"><span data-stu-id="f7919-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![此圖表顯示 LINQ to DataSet 以 ADO.NET 提供者為基礎。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="f7919-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="f7919-114">In This Section</span></span>  
 [<span data-ttu-id="f7919-115">快速入門</span><span class="sxs-lookup"><span data-stu-id="f7919-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="f7919-116">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="f7919-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="f7919-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="f7919-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="f7919-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7919-118">See also</span></span>

- [<span data-ttu-id="f7919-119">Language-Integrated Query (LINQ) - C#</span><span class="sxs-lookup"><span data-stu-id="f7919-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="f7919-120">Language-Integrated Query (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f7919-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="f7919-121">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f7919-121">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="f7919-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f7919-122">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
