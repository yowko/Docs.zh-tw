---
title: "部署 WCF 程式庫專案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04567b0b06ef5c8f105e866e150bfaa221d64057
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="7d074-102">部署 WCF 程式庫專案</span><span class="sxs-lookup"><span data-stu-id="7d074-102">Deploying a WCF Library Project</span></span>
<span data-ttu-id="7d074-103">本主題說明如何部署 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="7d074-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="7d074-104">部署 WCF 服務程式庫</span><span class="sxs-lookup"><span data-stu-id="7d074-104">Deploying a WCF Service Library</span></span>  
 <span data-ttu-id="7d074-105">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫是一種動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="7d074-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="7d074-106">因此，它無法自行執行，</span><span class="sxs-lookup"><span data-stu-id="7d074-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="7d074-107">而必須部署在裝載環境中。</span><span class="sxs-lookup"><span data-stu-id="7d074-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="7d074-108">如需此程序的詳細資訊，請參閱[主控和取用 WCF 服務](http://go.microsoft.com/fwlink/?LinkId=99932)。</span><span class="sxs-lookup"><span data-stu-id="7d074-108">For more information about this process, see [Hosting and Consuming WCF Services](http://go.microsoft.com/fwlink/?LinkId=99932).</span></span>  
  
 <span data-ttu-id="7d074-109">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫可以像任何其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務一樣來部署。</span><span class="sxs-lookup"><span data-stu-id="7d074-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library can be deployed like any other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="7d074-110">不過，請注意 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 不支援設定 DLL。</span><span class="sxs-lookup"><span data-stu-id="7d074-110">However, be aware that [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support configuration for DLLs.</span></span> <span data-ttu-id="7d074-111"><xref:System.Configuration> 針對每個應用程式定義域各支援一個組態檔。</span><span class="sxs-lookup"><span data-stu-id="7d074-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="7d074-112">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫專案藉由在開發期間為程式庫提供 App.config 檔案，來減輕此限制。</span><span class="sxs-lookup"><span data-stu-id="7d074-112">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="7d074-113">但是，部署後無法辨識 App.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="7d074-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="7d074-114">您必須將組態程式碼移至裝載環境所辨識的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="7d074-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="7d074-115">如果是自我裝載，則應該將 App.config 檔案的內容複製到裝載可執行檔的 App.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="7d074-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="7d074-116">如果您使用 IIS 裝載服務，您應該將 App.config 檔案的內容複製到虛擬目錄的 Web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="7d074-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
