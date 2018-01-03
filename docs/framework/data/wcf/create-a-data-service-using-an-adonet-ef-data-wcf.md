---
title: "如何：使用 ADO.NET Entity Framework 資料來源建立資料服務 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9362aa6ea02f5878d2419ee7cbaab349cae27038
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="ace3c-102">如何：使用 ADO.NET Entity Framework 資料來源建立資料服務 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="ace3c-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="ace3c-103"> 會將實體資料公開為資料服務。</span><span class="sxs-lookup"><span data-stu-id="ace3c-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="ace3c-104">當資料來源為關聯式資料庫時，這個實體資料會由 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 提供。</span><span class="sxs-lookup"><span data-stu-id="ace3c-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="ace3c-105">本主題示範如何在以現有資料庫為基礎的 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 應用程式中建立 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 架構資料模型，並使用此資料模型建立新的資料服務。</span><span class="sxs-lookup"><span data-stu-id="ace3c-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web application that is based on an existing database and use this data model to create a new data service.</span></span>  
  
 <span data-ttu-id="ace3c-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 也提供命令列工具，可在 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 專案以外產生 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 模型。</span><span class="sxs-lookup"><span data-stu-id="ace3c-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project.</span></span> <span data-ttu-id="ace3c-107">如需詳細資訊，請參閱[How to： 使用 EdmGen.exe 產生模型和對應檔](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="ace3c-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="ace3c-108">若要將以現有資料庫為基礎的 Entity Framework 模型加入至現有的 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="ace3c-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>  
  
1.  <span data-ttu-id="ace3c-109">在**專案**功能表上，按一下 **加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="ace3c-109">On the **Project** menu, click **Add new item**.</span></span>  
  
2.  <span data-ttu-id="ace3c-110">在**範本**] 窗格中，按一下 [**資料**類別目錄，然後選取**ADO.NET 實體資料模型**。</span><span class="sxs-lookup"><span data-stu-id="ace3c-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="ace3c-111">輸入模型名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="ace3c-111">Type the model name and then click **Add**.</span></span>  
  
     <span data-ttu-id="ace3c-112">[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] 精靈的第一頁隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ace3c-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>  
  
4.  <span data-ttu-id="ace3c-113">在**選擇模型內容**對話方塊中，選取**從資料庫產生**。</span><span class="sxs-lookup"><span data-stu-id="ace3c-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="ace3c-114">然後按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ace3c-114">Then click **Next**.</span></span>  
  
5.  <span data-ttu-id="ace3c-115">按一下**新連線** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ace3c-115">Click the **New Connection** button.</span></span>  
  
6.  <span data-ttu-id="ace3c-116">在**連接屬性**對話方塊中，輸入您的伺服器名稱、 選取驗證方法、 輸入資料庫名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ace3c-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ace3c-117">**選擇資料連接**的對話方塊會更新與您的資料庫連接設定。</span><span class="sxs-lookup"><span data-stu-id="ace3c-117">The **Choose Your Data Connection**s dialog box is updated with your database connection settings.</span></span>  
  
7.  <span data-ttu-id="ace3c-118">請確認**將實體連接設定儲存為 App.Config 中：**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ace3c-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="ace3c-119">然後按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ace3c-119">Then click **Next**.</span></span>  
  
8.  <span data-ttu-id="ace3c-120">在**選擇您的資料庫物件**對話方塊中，選取的所有資料庫物件想要在資料服務中公開。</span><span class="sxs-lookup"><span data-stu-id="ace3c-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ace3c-121">資料服務不會自動公開包含在資料模型中的物件，</span><span class="sxs-lookup"><span data-stu-id="ace3c-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="ace3c-122">必須由服務本身明確公開。</span><span class="sxs-lookup"><span data-stu-id="ace3c-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="ace3c-123">如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ace3c-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
9. <span data-ttu-id="ace3c-124">按一下**完成**以完成精靈。</span><span class="sxs-lookup"><span data-stu-id="ace3c-124">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="ace3c-125">這樣會根據特定資料庫建立預設資料模型。</span><span class="sxs-lookup"><span data-stu-id="ace3c-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="ace3c-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 可讓您自訂資料模型。</span><span class="sxs-lookup"><span data-stu-id="ace3c-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="ace3c-127">如需詳細資訊，請參閱[工作](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb)。</span><span class="sxs-lookup"><span data-stu-id="ace3c-127">For more information, see [Tasks](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span></span>  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="ace3c-128">若要使用新的資料模型建立資料服務</span><span class="sxs-lookup"><span data-stu-id="ace3c-128">To create the data service by using the new data model</span></span>  
  
1.  <span data-ttu-id="ace3c-129">在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 中，開啟代表該資料模型的 .edmx 檔案。</span><span class="sxs-lookup"><span data-stu-id="ace3c-129">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], open the .edmx file that represents the data model.</span></span>  
  
2.  <span data-ttu-id="ace3c-130">在**模型瀏覽器**、 以滑鼠右鍵按一下模型、 按一下**屬性**，然後記下實體容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="ace3c-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>  
  
3.  <span data-ttu-id="ace3c-131">在**方案總管 中**，以滑鼠右鍵按一下名稱您[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案，然後再按一下**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="ace3c-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
4.  <span data-ttu-id="ace3c-132">在**加入新項目**對話方塊中，選取**WCF 資料服務**。</span><span class="sxs-lookup"><span data-stu-id="ace3c-132">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
5.  <span data-ttu-id="ace3c-133">提供服務的名稱，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ace3c-133">Supply a name for the service, and then click **OK**.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="ace3c-134"> 會針對新的服務建立 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="ace3c-134"> creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="ace3c-135">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="ace3c-135">By default, the code-editor window opens.</span></span>  
  
6.  <span data-ttu-id="ace3c-136">在資料服務的程式碼中，以繼承自 `/* TODO: put your data source class name here */` 類別且為資料模型實體容器 (您已在步驟 2 中記下該容器) 的型別，取代定義資料服務之類別定義中的 <xref:System.Data.Objects.ObjectContext> 註解。</span><span class="sxs-lookup"><span data-stu-id="ace3c-136">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>  
  
7.  <span data-ttu-id="ace3c-137">在資料服務的程式碼中，啟用已授權的用戶端以存取資料服務所公開的實體集。</span><span class="sxs-lookup"><span data-stu-id="ace3c-137">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="ace3c-138">如需詳細資訊，請參閱[建立資料服務](../../../../docs/framework/data/wcf/creating-the-data-service.md)。</span><span class="sxs-lookup"><span data-stu-id="ace3c-138">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
8.  <span data-ttu-id="ace3c-139">若要使用網頁瀏覽器測試 Northwind.svc 資料服務，請遵循本主題中的指示[從網頁瀏覽器存取服務](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="ace3c-139">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace3c-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="ace3c-140">See Also</span></span>  
 [<span data-ttu-id="ace3c-141">定義 WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="ace3c-141">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="ace3c-142">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="ace3c-142">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="ace3c-143">如何：使用反映提供者建立資料服務</span><span class="sxs-lookup"><span data-stu-id="ace3c-143">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="ace3c-144">如何：使用 LINQ to SQL 資料來源建立資料服務</span><span class="sxs-lookup"><span data-stu-id="ace3c-144">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
