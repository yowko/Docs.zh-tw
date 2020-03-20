---
title: HOW TO：在 IIS 中裝載 WCF 服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184928"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="04f22-102">HOW TO：在 IIS 中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="04f22-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="04f22-103">本主題概述了創建 Internet 資訊服務 （IIS） 中託管的 Windows 通信基礎 （WCF） 服務所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="04f22-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="04f22-104">本主題假設您熟悉 IIS，而且了解如何使用 IIS 管理工具建立與管理 IIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="04f22-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="04f22-105">有關 IIS 的更多資訊，請參閱[互聯網資訊服務](https://www.iis.net/)。</span><span class="sxs-lookup"><span data-stu-id="04f22-105">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="04f22-106">在 IIS 環境中運行的 WCF 服務充分利用了 IIS 功能，例如進程回收、空閒關閉、過程運行狀況監視和基於消息的啟動。</span><span class="sxs-lookup"><span data-stu-id="04f22-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="04f22-107">這個裝載選項要求必須正確設定 IIS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="04f22-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="04f22-108">IIS 裝載只能和 HTTP 傳輸一起使用。</span><span class="sxs-lookup"><span data-stu-id="04f22-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="04f22-109">有關 WCF 和ASP.NET如何交互的詳細資訊，請參閱[WCF 服務和ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="04f22-109">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="04f22-110">有關配置安全性的詳細資訊，請參閱[安全](../../../../docs/framework/wcf/feature-details/security.md)。</span><span class="sxs-lookup"><span data-stu-id="04f22-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="04f22-111">有關此示例的源副本，請參閱[使用內聯代碼進行 IIS 託管](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)。</span><span class="sxs-lookup"><span data-stu-id="04f22-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="04f22-112">若要建立 IIS 裝載的服務</span><span class="sxs-lookup"><span data-stu-id="04f22-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="04f22-113">確認您的電腦上已安裝 IIS 且正在執行中。</span><span class="sxs-lookup"><span data-stu-id="04f22-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="04f22-114">有關安裝和配置 IIS 的詳細資訊，請參閱[安裝和配置 IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="04f22-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="04f22-115">為您的應用程式檔創建一個名為"IIS託管CalcService"的新資料夾，確保ASP.NET有權訪問該資料夾的內容，並使用 IIS 管理工具創建位於此應用程式目錄中的新 IIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="04f22-115">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="04f22-116">建立應用程式目錄的別名時，請使用 "IISHostedCalc"。</span><span class="sxs-lookup"><span data-stu-id="04f22-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="04f22-117">在應用程式目錄中建立名為 "service.svc" 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="04f22-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="04f22-118">通過添加以下@ServiceHost元素編輯此檔。</span><span class="sxs-lookup"><span data-stu-id="04f22-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="04f22-119">在應用程式目錄中建立 App_Code 子目錄。</span><span class="sxs-lookup"><span data-stu-id="04f22-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="04f22-120">在 App_Code 子目錄中建立名為 Service.cs 的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="04f22-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="04f22-121">使用陳述式將以下加入至 Service.cs 檔案的最上方。</span><span class="sxs-lookup"><span data-stu-id="04f22-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="04f22-122">使用陳述式之後，加入下列命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="04f22-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="04f22-123">在命名空間宣告內定義服務合約，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="04f22-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="04f22-124">在符合合約定義之後實作服務合約，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="04f22-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="04f22-125">在應用程式目錄中建立名為 "Web.config" 的檔案，並將下列組態程式碼加入至該檔案中。</span><span class="sxs-lookup"><span data-stu-id="04f22-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="04f22-126">在運行時，WCF 基礎結構使用資訊構造用戶端應用程式可以與其通信的終結點。</span><span class="sxs-lookup"><span data-stu-id="04f22-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="04f22-127">此範例會在組態檔中明確地指定端點。</span><span class="sxs-lookup"><span data-stu-id="04f22-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="04f22-128">如果您沒有將任何端點加入至服務中，執行階段會為您加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="04f22-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="04f22-129">有關預設終結點、綁定和行為的詳細資訊，請參閱 WCF 服務的[簡化配置](../../../../docs/framework/wcf/simplified-configuration.md)和[簡化配置](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04f22-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="04f22-130">若要確認服務裝載正確，請開啟 Internet Explorer 的執行個體，然後瀏覽到服務的 URL：`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="04f22-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="04f22-131">範例</span><span class="sxs-lookup"><span data-stu-id="04f22-131">Example</span></span>  
 <span data-ttu-id="04f22-132">以下是裝載於 IIS 之計算機服務的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="04f22-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="04f22-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04f22-133">See also</span></span>

- [<span data-ttu-id="04f22-134">在網際網路資訊服務中裝載</span><span class="sxs-lookup"><span data-stu-id="04f22-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="04f22-135">裝載服務</span><span class="sxs-lookup"><span data-stu-id="04f22-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="04f22-136">WCF 服務與 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="04f22-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="04f22-137">安全性</span><span class="sxs-lookup"><span data-stu-id="04f22-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
- <span data-ttu-id="04f22-138">[Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="04f22-138">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
