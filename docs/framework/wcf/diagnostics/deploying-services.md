---
title: "部署服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75069b00fa07078ff0eb2d49e64f046d5415d154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-services"></a><span data-ttu-id="1fa01-102">部署服務</span><span class="sxs-lookup"><span data-stu-id="1fa01-102">Deploying Services</span></span>
<span data-ttu-id="1fa01-103">本主題將說明如何將 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式部署到執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="1fa01-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="1fa01-104">為您的應用程式選擇裝載環境</span><span class="sxs-lookup"><span data-stu-id="1fa01-104">Choosing the Hosting Environment for Your Application</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1fa01-105"> 服務是設計為在支援 Managed 程式碼的 Windows 處理序中執行的。</span><span class="sxs-lookup"><span data-stu-id="1fa01-105"> services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="1fa01-106">如果要成為作用中的服務，必須將服務裝載在建立及控制其內容和存留時間的執行階段環境中。</span><span class="sxs-lookup"><span data-stu-id="1fa01-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="1fa01-107">裝載選項的範圍從在最簡單的主控台應用程式到伺服器環境 (如 Windows 服務、Internet Information Services (IIS)) 內執行，或在由 Windows Activation Service (WAS) 管理的背景工作處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="1fa01-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="1fa01-108">若要檢閱為不同的裝載選項您[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]應用程式，請參閱[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1fa01-108">To review the different hosting options for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa01-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fa01-109">See Also</span></span>  
 [<span data-ttu-id="1fa01-110">裝載</span><span class="sxs-lookup"><span data-stu-id="1fa01-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="1fa01-111">裝載服務</span><span class="sxs-lookup"><span data-stu-id="1fa01-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
