---
title: "HOW TO：部署 COM+ 整合應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aca9df2be74dba308d3c4e4eb1c61b3e1afaa580
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="01d0e-102">HOW TO：部署 COM+ 整合應用程式</span><span class="sxs-lookup"><span data-stu-id="01d0e-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="01d0e-103">撰寫好 COM+ 整合應用程式後，您可能會想要將它部署在其他機器上。</span><span class="sxs-lookup"><span data-stu-id="01d0e-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="01d0e-104">此主題描述如何將 COM+ 整合應用程式從一部機器移到另一部機器。</span><span class="sxs-lookup"><span data-stu-id="01d0e-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="01d0e-105">移動 COM+ 主控的整合應用程式</span><span class="sxs-lookup"><span data-stu-id="01d0e-105">Moving a COM+ hosted Integration App</span></span>  
  
1.  <span data-ttu-id="01d0e-106">請確定兩部機器上都已安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="01d0e-106">Ensure that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="01d0e-107">從機器 A 匯出應用程式。</span><span class="sxs-lookup"><span data-stu-id="01d0e-107">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="01d0e-108">將應用程式匯入機器 B。</span><span class="sxs-lookup"><span data-stu-id="01d0e-108">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="01d0e-109">設定應用程式根目錄。</span><span class="sxs-lookup"><span data-stu-id="01d0e-109">Set the Application Root Directory.</span></span> <span data-ttu-id="01d0e-110">根據慣例，根目錄是 %PROGRAMFILES%/ComPlus Applications/{AppGUID}。</span><span class="sxs-lookup"><span data-stu-id="01d0e-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5.  <span data-ttu-id="01d0e-111">從機器 A 的應用程式根目錄，將 Application.config 和 Application.manifest 檔案複製到機器 B 的應用程式根目錄。</span><span class="sxs-lookup"><span data-stu-id="01d0e-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6.  <span data-ttu-id="01d0e-112">在機器 B 的 Application.config 檔案中編輯服務端點位址，以識別適當的機器。</span><span class="sxs-lookup"><span data-stu-id="01d0e-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="01d0e-113">例如，將 http://machineA/MyService 變更為 http://machineB/MyService。</span><span class="sxs-lookup"><span data-stu-id="01d0e-113">For example, change http://machineA/MyService to http://machineB/MyService.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="01d0e-114">移動 Web 主控的整合應用程式</span><span class="sxs-lookup"><span data-stu-id="01d0e-114">Moving a Web-hosted integration application</span></span>  
  
1.  <span data-ttu-id="01d0e-115">請確定兩部機器上都已安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="01d0e-115">Ensure that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="01d0e-116">從機器 A 匯出應用程式。</span><span class="sxs-lookup"><span data-stu-id="01d0e-116">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="01d0e-117">將應用程式匯入機器 B。</span><span class="sxs-lookup"><span data-stu-id="01d0e-117">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="01d0e-118">在機器 B 上建立 IIS VRoot。</span><span class="sxs-lookup"><span data-stu-id="01d0e-118">Create an IIS vroot on machine B.</span></span>  
  
5.  <span data-ttu-id="01d0e-119">從機器 A 的 VRoot，將 .svc 檔 (componentName.svc) 和 Web.config 檔複製到機器 B 上新建立的 VRoot。</span><span class="sxs-lookup"><span data-stu-id="01d0e-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d0e-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="01d0e-120">See Also</span></span>  
 [<span data-ttu-id="01d0e-121">整合 COM+ 應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="01d0e-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [<span data-ttu-id="01d0e-122">如何：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="01d0e-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [<span data-ttu-id="01d0e-123">如何：使用 COM+ 服務模型組態工具</span><span class="sxs-lookup"><span data-stu-id="01d0e-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
