---
title: 部署 WCF 程式庫專案
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 186ce5ae3087fd9b4c7e5c32e110de4bc7d5e578
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801990"
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="86dd7-102">部署 WCF 程式庫專案</span><span class="sxs-lookup"><span data-stu-id="86dd7-102">Deploying a WCF Library Project</span></span>
<span data-ttu-id="86dd7-103">本主題說明如何部署 Windows Communication Foundation （WCF）服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="86dd7-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="86dd7-104">部署 WCF 服務程式庫</span><span class="sxs-lookup"><span data-stu-id="86dd7-104">Deploying a WCF Service Library</span></span>  
 <span data-ttu-id="86dd7-105">WCF 服務程式庫是一種動態連結程式庫（DLL）。</span><span class="sxs-lookup"><span data-stu-id="86dd7-105">A WCF service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="86dd7-106">因此，它無法自行執行，</span><span class="sxs-lookup"><span data-stu-id="86dd7-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="86dd7-107">而必須部署在裝載環境中。</span><span class="sxs-lookup"><span data-stu-id="86dd7-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="86dd7-108">如需此流程的詳細資訊，請參閱[裝載和使用 WCF 服務](https://docs.microsoft.com/previous-versions/dotnet/articles/bb332338(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="86dd7-108">For more information about this process, see [Hosting and Consuming WCF Services](https://docs.microsoft.com/previous-versions/dotnet/articles/bb332338(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="86dd7-109">WCF 服務程式庫可以像任何其他 WCF 服務一樣部署。</span><span class="sxs-lookup"><span data-stu-id="86dd7-109">A WCF service library can be deployed like any other WCF service.</span></span> <span data-ttu-id="86dd7-110">不過，請注意，.NET Framework 不支援 Dll 的設定。</span><span class="sxs-lookup"><span data-stu-id="86dd7-110">However, be aware that .NET Framework does not support configuration for DLLs.</span></span> <span data-ttu-id="86dd7-111"><xref:System.Configuration> 針對每個應用程式定義域各支援一個組態檔。</span><span class="sxs-lookup"><span data-stu-id="86dd7-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="86dd7-112">WCF 服務程式庫專案會在開發期間提供程式庫的 App.config 檔案，以減輕這項限制。</span><span class="sxs-lookup"><span data-stu-id="86dd7-112">The WCF service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="86dd7-113">但是，部署後無法辨識 App.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="86dd7-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="86dd7-114">您必須將組態程式碼移至裝載環境所辨識的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="86dd7-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="86dd7-115">如果是自我裝載，則應該將 App.config 檔案的內容複製到裝載可執行檔的 App.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="86dd7-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="86dd7-116">如果您使用 IIS 裝載服務，您應該將 App.config 檔案的內容複製到虛擬目錄的 Web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="86dd7-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
