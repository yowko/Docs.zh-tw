---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 1c03cca80de6003a4e49278871983ed7fcb3dc0b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200662"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="f4ce8-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f4ce8-102">LINQ to DataSet</span></span>

<span data-ttu-id="f4ce8-103">LINQ to DataSet 可讓您更輕鬆且更快速地查詢在物件中快取的資料 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="f4ce8-104">具體來說，LINQ to DataSet 可讓開發人員從程式設計語言本身撰寫查詢，而不是使用不同的查詢語言，藉以簡化查詢。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="f4ce8-105">這特別適用于 Visual Studio 開發人員，他們現在可以利用查詢中 Visual Studio 所提供的編譯時期語法檢查、靜態類型和 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="f4ce8-106">LINQ to DataSet 也可以用來查詢已從一或多個資料來源合併的資料。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="f4ce8-107">這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="f4ce8-108">尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="f4ce8-109">LINQ to DataSet 的功能主要是透過和類別中的擴充方法來公開 <xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions> 。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="f4ce8-110">LINQ to DataSet 建基於並使用現有的 ADO.NET 架構，而不是用來取代應用程式程式碼中的 ADO.NET。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="f4ce8-111">現有的 ADO.NET 程式碼將繼續在 LINQ to DataSet 應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="f4ce8-112">下圖將說明 LINQ to DataSet 與 ADO.NET 以及資料存放區的關聯性。</span><span class="sxs-lookup"><span data-stu-id="f4ce8-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![顯示 LINQ to DataSet 以 ADO.NET 提供者為基礎的圖表。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="f4ce8-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="f4ce8-114">In This Section</span></span>  

 [<span data-ttu-id="f4ce8-115">快速入門</span><span class="sxs-lookup"><span data-stu-id="f4ce8-115">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="f4ce8-116">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f4ce8-116">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="f4ce8-117">參考</span><span class="sxs-lookup"><span data-stu-id="f4ce8-117">Reference</span></span>  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="f4ce8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4ce8-118">See also</span></span>

- [<span data-ttu-id="f4ce8-119">Language-Integrated Query (LINQ) - C#</span><span class="sxs-lookup"><span data-stu-id="f4ce8-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="f4ce8-120">Language-Integrated Query (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4ce8-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="f4ce8-121">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f4ce8-121">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="f4ce8-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f4ce8-122">ADO.NET</span></span>](index.md)
