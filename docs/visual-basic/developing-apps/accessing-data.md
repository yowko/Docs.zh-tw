---
title: "在 Visual Basic 應用程式中存取資料"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data [Visual Basic]
- Visual Basic, data access
ms.assetid: 3086ab38-3be5-4b22-9385-7d0e16b04f6a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae0611fdadabd6ab684f3f97995f3be3e348e648
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="2f8ce-102">在 Visual Basic 應用程式中存取資料</span><span class="sxs-lookup"><span data-stu-id="2f8ce-102">Accessing data in Visual Basic applications</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="2f8ce-103"> 包括數個新功能，以協助開發可存取資料的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-103"> includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="2f8ce-104">將項目從[資料來源視窗](/visualstudio/data-tools/add-new-data-sources)拖曳至表單，以建立 Windows 應用程式的資料繫結表單。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="2f8ce-105">將項目從 [資料來源] 視窗拖曳至現有控制項，以將控制項繫結至資料。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2f8ce-106">相關章節</span><span class="sxs-lookup"><span data-stu-id="2f8ce-106">Related sections</span></span>  
 [<span data-ttu-id="2f8ce-107">存取 Visual Studio 中的資料</span><span class="sxs-lookup"><span data-stu-id="2f8ce-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
 <span data-ttu-id="2f8ce-108">提供頁面的連結，這些頁面討論如何將資料存取功能納入應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

 [<span data-ttu-id="2f8ce-109">適用於 .NET 的 Visual Studio Data Tools</span><span class="sxs-lookup"><span data-stu-id="2f8ce-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
 <span data-ttu-id="2f8ce-110">提供頁面的連結，這些頁面與使用 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 建立可處理資料的應用程式相關。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-110">Provides links to pages on creating applications that work with data, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
 [<span data-ttu-id="2f8ce-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="2f8ce-111">LINQ</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="2f8ce-112">提供主題的連結，這些主題描述如何搭配使用 LINQ 與 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>  
  
 [<span data-ttu-id="2f8ce-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2f8ce-113">LINQ to SQL</span></span>](../../framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="2f8ce-114">提供 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2f8ce-115">包括程式設計範例。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-115">Includes programming examples.</span></span>  
  
 <span data-ttu-id="2f8ce-116">[LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) (Visual Studio 中的 LINQ to SQL 工具)</span><span class="sxs-lookup"><span data-stu-id="2f8ce-116">[LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)</span></span>  
 <span data-ttu-id="2f8ce-117">提供主題的連結，這些主題與如何在應用程式中建立 [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) 物件模型相關。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-117">Provides links to topics about how to create a [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) object model in applications.</span></span>  
  
 [<span data-ttu-id="2f8ce-118">使用多層式架構 (N-Tier) 應用程式中的資料集</span><span class="sxs-lookup"><span data-stu-id="2f8ce-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
 <span data-ttu-id="2f8ce-119">提供主題的連結，這些主題與如何建立多層資料應用程式相關。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-119">Provides links to topics about how to create multitiered data applications.</span></span>  
     
 [<span data-ttu-id="2f8ce-120">新增連線</span><span class="sxs-lookup"><span data-stu-id="2f8ce-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
 <span data-ttu-id="2f8ce-121">提供頁面的連結，這些頁面與使用 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 以利用設計階段工具和 ADO.NET 連線物件將應用程式連線至資料相關。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  

 [<span data-ttu-id="2f8ce-122">Visual Studio 中的資料集工具</span><span class="sxs-lookup"><span data-stu-id="2f8ce-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
 <span data-ttu-id="2f8ce-123">提供頁面的連結，這些頁面描述如何將資料載入資料集以及如何執行 SQL 陳述式和預存程序。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  
  
 [<span data-ttu-id="2f8ce-124">將控制項繫結至 Visual Studio 中的資料</span><span class="sxs-lookup"><span data-stu-id="2f8ce-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
 <span data-ttu-id="2f8ce-125">提供頁面的連結，這些頁面說明如何透過資料繫結控制項在 Windows Forms 上顯示資料。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>  
  
 [<span data-ttu-id="2f8ce-126">編輯資料集中的資料</span><span class="sxs-lookup"><span data-stu-id="2f8ce-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
 <span data-ttu-id="2f8ce-127">提供頁面的連結，這些頁面描述如何操作資料集之資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  
  
 [<span data-ttu-id="2f8ce-128">驗證資料集中的資料</span><span class="sxs-lookup"><span data-stu-id="2f8ce-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
 <span data-ttu-id="2f8ce-129">提供頁面的連結，這些頁面描述如何在資料行和資料列變更期間將驗證新增至資料集。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>  
  
 [<span data-ttu-id="2f8ce-130">將資料儲存回資料庫</span><span class="sxs-lookup"><span data-stu-id="2f8ce-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
 <span data-ttu-id="2f8ce-131">提供頁面的連結，這些頁面說明如何將已更新資料從應用程式傳送至資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>  
  
 [<span data-ttu-id="2f8ce-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2f8ce-132">ADO.NET</span></span>](../../framework/data/adonet/index.md)  
 <span data-ttu-id="2f8ce-133">描述 ADO.NET 類別，此類別會將資料存取服務公開給 .NET Framework 程式設計人員。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

 [<span data-ttu-id="2f8ce-134">Office 方案的資料</span><span class="sxs-lookup"><span data-stu-id="2f8ce-134">Data in Office Solutions</span></span>](https://msdn.microsoft.com/library/xx069ybh)  
 <span data-ttu-id="2f8ce-135">包含頁面的連結，這些頁面說明資料在 Office 方案中的運作方式，包括結構描述導向的程式設計、資料快取，以及伺服器端的資料存取。</span><span class="sxs-lookup"><span data-stu-id="2f8ce-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
