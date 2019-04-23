---
title: 部署服務
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 2c3cd17b597fafcd02b9155089bc583fafbc9dea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085748"
---
# <a name="deploying-services"></a><span data-ttu-id="5603e-102">部署服務</span><span class="sxs-lookup"><span data-stu-id="5603e-102">Deploying Services</span></span>
<span data-ttu-id="5603e-103">本主題說明您如何能夠部署到執行階段環境的 Windows Communication Foundation (WCF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5603e-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="5603e-104">為您的應用程式選擇裝載環境</span><span class="sxs-lookup"><span data-stu-id="5603e-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="5603e-105">WCF 服務專為在支援 managed 程式碼在任何 Windows 處理程序中執行。</span><span class="sxs-lookup"><span data-stu-id="5603e-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="5603e-106">如果要成為作用中的服務，必須將服務裝載在建立及控制其內容和存留時間的執行階段環境中。</span><span class="sxs-lookup"><span data-stu-id="5603e-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="5603e-107">裝載選項的範圍從在最簡單的主控台應用程式到伺服器環境 (如 Windows 服務、Internet Information Services (IIS)) 內執行，或在由 Windows Activation Service (WAS) 管理的背景工作處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="5603e-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="5603e-108">若要檢閱您的 WCF 應用程式的不同裝載選項，請參閱[裝載的服務](../../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5603e-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5603e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5603e-109">See also</span></span>

- [<span data-ttu-id="5603e-110">裝載</span><span class="sxs-lookup"><span data-stu-id="5603e-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)
- [<span data-ttu-id="5603e-111">裝載服務</span><span class="sxs-lookup"><span data-stu-id="5603e-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
