---
title: 作法：在 IIS 中裝載 WCF 服務
description: 瞭解如何建立裝載于 Internet Information Services (IIS) 的 WCF 服務。 IIS 裝載只能和 HTTP 傳輸一起使用。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 30910d428ddace7a5d5fc10fc0def21ea14d39c9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555994"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="e5a79-104">作法：在 IIS 中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="e5a79-104">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="e5a79-105">本主題概述在 Internet Information Services (IIS) 中，建立 Windows Communication Foundation (WCF) 服務所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="e5a79-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="e5a79-106">本主題假設您熟悉 IIS，而且了解如何使用 IIS 管理工具建立與管理 IIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5a79-106">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="e5a79-107">如需 IIS 的詳細資訊，請參閱 [Internet Information Services](https://www.iis.net/)。</span><span class="sxs-lookup"><span data-stu-id="e5a79-107">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="e5a79-108">在 IIS 環境中執行的 WCF 服務會充分利用 IIS 功能，例如進程回收、閒置關機、進程健康情況監視，以及訊息型啟用。</span><span class="sxs-lookup"><span data-stu-id="e5a79-108">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="e5a79-109">這個裝載選項要求必須正確設定 IIS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="e5a79-109">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="e5a79-110">IIS 裝載只能和 HTTP 傳輸一起使用。</span><span class="sxs-lookup"><span data-stu-id="e5a79-110">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="e5a79-111">如需 WCF 和 ASP.NET 如何互動的詳細資訊，請參閱 [Wcf 服務和 ASP.NET](wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a79-111">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="e5a79-112">如需設定安全性的詳細資訊，請參閱 [安全性](security.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a79-112">For more information about configuring security, see [Security](security.md).</span></span>  
  
 <span data-ttu-id="e5a79-113">如需此範例的來源複本，請參閱 [使用內嵌程式碼的 IIS 裝載](../samples/iis-hosting-using-inline-code.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a79-113">For the source copy of this example, see [IIS Hosting Using Inline Code](../samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="e5a79-114">若要建立 IIS 裝載的服務</span><span class="sxs-lookup"><span data-stu-id="e5a79-114">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="e5a79-115">確認您的電腦上已安裝 IIS 且正在執行中。</span><span class="sxs-lookup"><span data-stu-id="e5a79-115">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="e5a79-116">如需安裝和設定 IIS 的詳細資訊，請參閱 [安裝和設定 iis 7.0](/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="e5a79-116">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="e5a79-117">為您的應用程式檔建立稱為 "IISHostedCalcService" 的新資料夾，確認 ASP.NET 可存取資料夾的內容，並使用 IIS 管理工具來建立實際位於此應用程式目錄中的新 IIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5a79-117">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="e5a79-118">建立應用程式目錄的別名時，請使用 "IISHostedCalc"。</span><span class="sxs-lookup"><span data-stu-id="e5a79-118">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="e5a79-119">在應用程式目錄中建立名為 "service.svc" 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="e5a79-119">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="e5a79-120">藉由新增下列元素來編輯此檔案 @ServiceHost 。</span><span class="sxs-lookup"><span data-stu-id="e5a79-120">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="e5a79-121">在應用程式目錄中建立 App_Code 子目錄。</span><span class="sxs-lookup"><span data-stu-id="e5a79-121">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="e5a79-122">在 App_Code 子目錄中建立名為 Service.cs 的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="e5a79-122">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="e5a79-123">使用陳述式將以下加入至 Service.cs 檔案的最上方。</span><span class="sxs-lookup"><span data-stu-id="e5a79-123">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="e5a79-124">使用陳述式之後，加入下列命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="e5a79-124">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="e5a79-125">在命名空間宣告內定義服務合約，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e5a79-125">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="e5a79-126">在符合合約定義之後實作服務合約，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e5a79-126">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="e5a79-127">在應用程式目錄中建立名為 "Web.config" 的檔案，並將下列組態程式碼加入至該檔案中。</span><span class="sxs-lookup"><span data-stu-id="e5a79-127">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="e5a79-128">在執行時間，WCF 基礎結構會使用此資訊來建立用戶端應用程式可以通訊的端點。</span><span class="sxs-lookup"><span data-stu-id="e5a79-128">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="e5a79-129">此範例會在組態檔中明確地指定端點。</span><span class="sxs-lookup"><span data-stu-id="e5a79-129">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="e5a79-130">如果您沒有將任何端點加入至服務中，執行階段會為您加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="e5a79-130">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="e5a79-131">如需預設端點、系結和行為的詳細資訊，請參閱[簡化](../simplified-configuration.md)[的 WCF 服務設定和簡化的](../samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="e5a79-131">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="e5a79-132">若要確認服務裝載正確，請開啟 Internet Explorer 的執行個體，然後瀏覽到服務的 URL：`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="e5a79-132">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5a79-133">範例</span><span class="sxs-lookup"><span data-stu-id="e5a79-133">Example</span></span>  
 <span data-ttu-id="e5a79-134">以下是裝載於 IIS 之計算機服務的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="e5a79-134">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="e5a79-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5a79-135">See also</span></span>

- [<span data-ttu-id="e5a79-136">在網際網路資訊服務中裝載</span><span class="sxs-lookup"><span data-stu-id="e5a79-136">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="e5a79-137">裝載服務</span><span class="sxs-lookup"><span data-stu-id="e5a79-137">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="e5a79-138">WCF 服務與 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e5a79-138">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="e5a79-139">安全性</span><span class="sxs-lookup"><span data-stu-id="e5a79-139">Security</span></span>](security.md)
- <span data-ttu-id="e5a79-140">[Windows Server AppFabric 裝載功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e5a79-140">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
