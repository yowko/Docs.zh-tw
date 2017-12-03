---
title: "表單張貼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0fe1f8641de2b4ee504deeae8f97b312dfe9b99
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="form-post"></a><span data-ttu-id="4d7fa-102">表單張貼</span><span class="sxs-lookup"><span data-stu-id="4d7fa-102">Form Post</span></span>
<span data-ttu-id="4d7fa-103">這個範例示範如何擴充 WCF REST 程式設計模型，以支援新的傳入要求格式。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-103">This sample demonstrates how to extend the WCF REST programming model to support new incoming request formats.</span></span> <span data-ttu-id="4d7fa-104">這個範例還包括格式子的實作，可將 HTML 表單張貼的要求還原序列化為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類型。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-104">The sample also includes an implementation of a formatter that can deserialize a request from an HTML form post into a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type.</span></span> <span data-ttu-id="4d7fa-105">此外，這個範例使用 T4 範本傳回 HTML 頁面，該頁面提供可讓使用者回傳至 WCF REST 服務的 HTML 表單。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-105">In addition, the sample uses a T4 Template to return an HTML page, which provides the HTML form that users can post back to the WCF REST service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4d7fa-106">示範</span><span class="sxs-lookup"><span data-stu-id="4d7fa-106">Demonstrates</span></span>  
  
-   <span data-ttu-id="4d7fa-107">延伸對傳入要求格式的支援。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-107">Extending support for incoming request formats.</span></span>  
  
-   <span data-ttu-id="4d7fa-108">整合 T4 範本。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-108">Integrating T4 templates.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4d7fa-109">討論</span><span class="sxs-lookup"><span data-stu-id="4d7fa-109">Discussion</span></span>  
 <span data-ttu-id="4d7fa-110">此範例包含兩個專案。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-110">This sample consists of two projects.</span></span> <span data-ttu-id="4d7fa-111">一個專案是包括自訂要求格式子的 HtmlFormProcessing 程式庫，該格式子可將 HTML 表單張貼還原序列化為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類型。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-111">One project is the HtmlFormProcessing library that includes a custom request formatter that can deserialize HTML form posts into [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types.</span></span> <span data-ttu-id="4d7fa-112">另一個專案是主控台應用程式，它會擴充「基本資源服務」範例以使用 HtmlFormProcessing 程式庫的自訂要求格式子。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-112">The second project is a console application that extends the Basic Resource Service sample to use the custom request formatter of the HtmlFormProcessing library.</span></span>  
  
 <span data-ttu-id="4d7fa-113">可還原序列化 HTML 表單張貼的自訂格式子 (HtmlFormRequestDispatchFormatter) 同時接受兩種類型，一種是可以使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 從字串轉換的 <xref:System.ServiceModel.Dispatcher.QueryStringConverter> 類型，另一種是以 <xref:System.Runtime.Serialization.DataContractAttribute> 標記的類型，它只有可使用 QueryStringConverter 從字串轉換的成員。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-113">The custom formatter that can deserialize HTML form posts (HtmlFormRequestDispatchFormatter) accepts both [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that can be converted from a string using the <xref:System.ServiceModel.Dispatcher.QueryStringConverter> and types marked with <xref:System.Runtime.Serialization.DataContractAttribute> that only have members that can be converted from a string using the QueryStringConverter.</span></span>  
  
 <span data-ttu-id="4d7fa-114">HtmlFormProcessing 程式庫專案還包括抽象基底類別 `RequestBodyDispatchFormatter`，可用來建立其他自訂要求格式子。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-114">The HtmlFormProcessing library project also includes an abstract base class, `RequestBodyDispatchFormatter`, which can be used to create other custom request formatters.</span></span> <span data-ttu-id="4d7fa-115">衍生自 `RequestBodyDispatchFormatter` 的方式可讓開發人員著重於要求主體還原序列化邏輯，該邏輯可讓基底類別將 URI 範本參數對應至作業的方法參數。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-115">Deriving from the `RequestBodyDispatchFormatter` allows a developer to focus on the request body deserialization logic, which allows the base class to map the URI template parameters to the operation’s method parameters.</span></span> <span data-ttu-id="4d7fa-116">另外，HtmlFormProcessing 程式庫專案還包括 `HtmlFormProcessingBehavior` 類別，該類別會示範如何衍生自 <xref:System.ServiceModel.Description.WebHttpBehavior>，以便將預設要求格式子取代為自訂要求格式子。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-116">Also in the HtmlFormProcessing library project is the `HtmlFormProcessingBehavior` class, which demonstrates how to derive from the <xref:System.ServiceModel.Description.WebHttpBehavior> to replace the default request formatter with a custom request formatter.</span></span>  
  
 <span data-ttu-id="4d7fa-117">此主控台應用程式專案擴充[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-117">This console application project extends the [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample.</span></span> <span data-ttu-id="4d7fa-118">「基本資源服務」範例會示範如何以使用 WCF REST 程式設計模型的方式公開資源。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-118">The Basic Resource Service sample demonstrates how to expose a resource in a manner that uses the WCF REST programming model.</span></span> <span data-ttu-id="4d7fa-119">在「基本資源服務」範例中會公開客戶集合資源，以便建立、擷取、更新和刪除集合中的客戶。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-119">In the Basic Resource Service sample, a customer collection resource is exposed such that customers in the collection can be created, retrieved, updated and deleted.</span></span> <span data-ttu-id="4d7fa-120">「基本資源服務」範例僅使用兩種原本就支援的傳入要求格式：XML 和 JSON。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-120">The Basic Resource Service sample only uses the two natively supported incoming request formats, XML and JSON.</span></span>  
  
 <span data-ttu-id="4d7fa-121">在這個「表單張貼」範例中的主控台應用程式會利用 HtmlFormProcessing 程式庫中的自訂格式子，該程式庫可讓使用者使用瀏覽器從 HTML 表單張貼傳送要求，藉此建立客戶。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-121">The console application in this Form Post sample utilizes the custom formatter in the HtmlFormProcessing library, which allows users to create customers by sending a request from an HTML form post using a browser.</span></span> <span data-ttu-id="4d7fa-122">它還會加入傳回 HTML 頁面的作業，該頁面包括回傳至服務的表單。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-122">It also adds an operation that returns an HTML page, which includes the form to be posted back to the service.</span></span> <span data-ttu-id="4d7fa-123">這個 HTML 頁面是使用預先處理的 T4 範本產生，而這個範本是由 .tt 檔和自動產生的 .cs 檔所組成。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-123">This HTML page is generated using a preprocessed T4 template, which consists of a .tt file and an auto-generated .cs file.</span></span> <span data-ttu-id="4d7fa-124">.tt 檔可讓開發人員以包含變數和控制項結構的範本形式撰寫回應。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-124">The .tt file allows a developer to write a response in a template form that contains variables and control structures.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4d7fa-125">T4，請參閱[所使用文字範本產生成品](http://go.microsoft.com/fwlink/?LinkId=178139)。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-125"> T4, see [Generating Artifacts By Using Text Templates](http://go.microsoft.com/fwlink/?LinkId=178139).</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="4d7fa-126">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="4d7fa-126">To run the sample</span></span>  
  
1.  <span data-ttu-id="4d7fa-127">開啟「表單張貼範例」的方案。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-127">Open the solution for the Form Post Sample.</span></span> <span data-ttu-id="4d7fa-128">啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 時，您必須以系統管理員身分執行，才能成功執行範例。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-128">When launching [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], you must run as an administrator to execute the sample successfully.</span></span> <span data-ttu-id="4d7fa-129">執行這項操作，以滑鼠右鍵按一下[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]圖示，然後從內容功能表中選擇 「 系統管理員身分執行 」。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-129">Do this by right-clicking the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] icon and choosing "Run as Administrator" from the context menu.</span></span>  
  
2.  <span data-ttu-id="4d7fa-130">按下 CTRL+SHIFT+B 建置方案，然後按下 CTRL+F5 執行主控台應用程式 FormPost 專案。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-130">Press CTRL+SHIFT+B to build the solution and then press CTRL+F5 to run the console application FormPost project.</span></span>  
  
3.  <span data-ttu-id="4d7fa-131">主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-131">The console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span>  
  
4.  <span data-ttu-id="4d7fa-132">範例執行時，用戶端將目前活動的狀態 (無論是加入客戶、更新客戶、刪除客戶或取得目前客戶的清單) 從服務寫入至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-132">As the sample runs, the client writes the status of the current activity, whether it be adding a customer, updating a customer, deleting a customer or getting a list of current customers from the service to the console window.</span></span>  
  
5.  <span data-ttu-id="4d7fa-133">接著會提示您瀏覽至客戶表單的 URI。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-133">You are then prompted to browse to the URI of the customer form.</span></span> <span data-ttu-id="4d7fa-134">開啟瀏覽器並瀏覽至指定的 URI。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-134">Open a browser and browse to the given URI.</span></span> <span data-ttu-id="4d7fa-135">輸入名稱和地址做為客戶按一下**送出** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-135">Type in a name and address for the customer and click the **Submit** button.</span></span>  
  
6.  <span data-ttu-id="4d7fa-136">按下主控台視窗的任意鍵，即可繼續執行範例。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-136">Press any key for the console window to continue running the sample.</span></span>  
  
7.  <span data-ttu-id="4d7fa-137">範例完成時，請注意您使用瀏覽器建立的客戶會包含在最終客戶清單內。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-137">As the sample completes, notice that the customer you created using the browser is included in the final list of customers.</span></span>  
  
8.  <span data-ttu-id="4d7fa-138">按下任何按鍵可終止此範例。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-138">Press any key to terminate the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d7fa-139">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d7fa-140">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d7fa-141">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d7fa-142">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4d7fa-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
