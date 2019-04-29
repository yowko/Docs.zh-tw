---
title: HOW TO：部署 COM+ 整合應用程式
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: fcf525943e6e453253c6f4d3bcfa8a1a08df6909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778322"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="32ac1-102">HOW TO：部署 COM+ 整合應用程式</span><span class="sxs-lookup"><span data-stu-id="32ac1-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="32ac1-103">撰寫好 COM+ 整合應用程式後，您可能會想要將它部署在其他機器上。</span><span class="sxs-lookup"><span data-stu-id="32ac1-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="32ac1-104">此主題描述如何將 COM+ 整合應用程式從一部機器移到另一部機器。</span><span class="sxs-lookup"><span data-stu-id="32ac1-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="32ac1-105">移動 COM+ 主控的整合應用程式</span><span class="sxs-lookup"><span data-stu-id="32ac1-105">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="32ac1-106">請確定兩台電腦上已安裝 WCF。</span><span class="sxs-lookup"><span data-stu-id="32ac1-106">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="32ac1-107">從機器 A 匯出應用程式。</span><span class="sxs-lookup"><span data-stu-id="32ac1-107">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="32ac1-108">將應用程式匯入機器 B。</span><span class="sxs-lookup"><span data-stu-id="32ac1-108">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="32ac1-109">設定應用程式根目錄。</span><span class="sxs-lookup"><span data-stu-id="32ac1-109">Set the Application Root Directory.</span></span> <span data-ttu-id="32ac1-110">根據慣例，根目錄是 %PROGRAMFILES%/ComPlus Applications/{AppGUID}。</span><span class="sxs-lookup"><span data-stu-id="32ac1-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="32ac1-111">從機器 A 的應用程式根目錄，將 Application.config 和 Application.manifest 檔案複製到機器 B 的應用程式根目錄。</span><span class="sxs-lookup"><span data-stu-id="32ac1-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="32ac1-112">在機器 B 的 Application.config 檔案中編輯服務端點位址，以識別適當的機器。</span><span class="sxs-lookup"><span data-stu-id="32ac1-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="32ac1-113">例如，將 `http://machineA/MyService` 變更為 `http://machineB/MyService`。</span><span class="sxs-lookup"><span data-stu-id="32ac1-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="32ac1-114">移動 Web 主控的整合應用程式</span><span class="sxs-lookup"><span data-stu-id="32ac1-114">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="32ac1-115">請確定兩台電腦上已安裝 WCF。</span><span class="sxs-lookup"><span data-stu-id="32ac1-115">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="32ac1-116">從機器 A 匯出應用程式。</span><span class="sxs-lookup"><span data-stu-id="32ac1-116">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="32ac1-117">將應用程式匯入機器 B。</span><span class="sxs-lookup"><span data-stu-id="32ac1-117">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="32ac1-118">在機器 B 上建立 IIS VRoot。</span><span class="sxs-lookup"><span data-stu-id="32ac1-118">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="32ac1-119">從機器 A 的 VRoot，將 .svc 檔 (componentName.svc) 和 Web.config 檔複製到機器 B 上新建立的 VRoot。</span><span class="sxs-lookup"><span data-stu-id="32ac1-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ac1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32ac1-120">See also</span></span>

- [<span data-ttu-id="32ac1-121">整合 COM+ 應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="32ac1-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="32ac1-122">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="32ac1-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [<span data-ttu-id="32ac1-123">如何：使用 COM + 服務模型組態工具</span><span class="sxs-lookup"><span data-stu-id="32ac1-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
