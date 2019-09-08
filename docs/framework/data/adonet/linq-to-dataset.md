---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783782"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="ce136-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="ce136-102">LINQ to DataSet</span></span>
<span data-ttu-id="ce136-103">LINQ to DataSet 可讓您更輕鬆且更快速地查詢在<xref:System.Data.DataSet>物件中快取的資料。</span><span class="sxs-lookup"><span data-stu-id="ce136-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="ce136-104">具體而言，LINQ to DataSet 可讓開發人員從程式設計語言本身撰寫查詢，而不是使用不同的查詢語言，藉此簡化查詢。</span><span class="sxs-lookup"><span data-stu-id="ce136-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="ce136-105">這對於 Visual Studio 開發人員特別有用，他們現在可以利用查詢中 Visual Studio 所提供的編譯時間語法檢查、靜態型別和 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="ce136-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="ce136-106">LINQ to DataSet 也可以用來查詢已從一個或多個資料來源合併的資料。</span><span class="sxs-lookup"><span data-stu-id="ce136-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="ce136-107">這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。</span><span class="sxs-lookup"><span data-stu-id="ce136-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="ce136-108">尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。</span><span class="sxs-lookup"><span data-stu-id="ce136-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="ce136-109">LINQ to DataSet 功能主要是透過<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別中的擴充方法公開。</span><span class="sxs-lookup"><span data-stu-id="ce136-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="ce136-110">LINQ to DataSet 是以現有的 ADO.NET 架構為基礎，而不是用來取代應用程式程式碼中的 ADO.NET。</span><span class="sxs-lookup"><span data-stu-id="ce136-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="ce136-111">現有的 ADO.NET 程式碼會繼續在 LINQ to DataSet 應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="ce136-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="ce136-112">下圖說明 LINQ to DataSet ADO.NET 與資料存放區的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ce136-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![此圖顯示 LINQ to DataSet 是以 ADO.NET 提供者為基礎。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="ce136-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="ce136-114">In This Section</span></span>  
 [<span data-ttu-id="ce136-115">快速入門</span><span class="sxs-lookup"><span data-stu-id="ce136-115">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="ce136-116">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="ce136-116">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="ce136-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="ce136-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="ce136-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce136-118">See also</span></span>

- [<span data-ttu-id="ce136-119">Language-Integrated Query (LINQ) - C#</span><span class="sxs-lookup"><span data-stu-id="ce136-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="ce136-120">Language-Integrated Query (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce136-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="ce136-121">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce136-121">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="ce136-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce136-122">ADO.NET</span></span>](index.md)
