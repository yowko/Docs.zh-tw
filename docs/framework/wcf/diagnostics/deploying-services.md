---
title: 部署服務
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 684b781c568518cfb321d8021e4f7062e855e6aa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798137"
---
# <a name="deploying-services"></a><span data-ttu-id="31989-102">部署服務</span><span class="sxs-lookup"><span data-stu-id="31989-102">Deploying Services</span></span>
<span data-ttu-id="31989-103">本主題說明如何將 Windows Communication Foundation （WCF）應用程式部署至執行時間環境。</span><span class="sxs-lookup"><span data-stu-id="31989-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="31989-104">為您的應用程式選擇裝載環境</span><span class="sxs-lookup"><span data-stu-id="31989-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="31989-105">WCF 服務是設計用來在任何支援 managed 程式碼的 Windows 進程中執行。</span><span class="sxs-lookup"><span data-stu-id="31989-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="31989-106">如果要成為作用中的服務，必須將服務裝載在建立及控制其內容和存留時間的執行階段環境中。</span><span class="sxs-lookup"><span data-stu-id="31989-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="31989-107">裝載選項的範圍從在最簡單的主控台應用程式到伺服器環境 (如 Windows 服務、Internet Information Services (IIS)) 內執行，或在由 Windows Activation Service (WAS) 管理的背景工作處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="31989-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="31989-108">若要查看 WCF 應用程式的不同裝載選項，請參閱[裝載服務](../hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="31989-108">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31989-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31989-109">See also</span></span>

- [<span data-ttu-id="31989-110">裝載</span><span class="sxs-lookup"><span data-stu-id="31989-110">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="31989-111">裝載服務</span><span class="sxs-lookup"><span data-stu-id="31989-111">Hosting Services</span></span>](../hosting-services.md)
