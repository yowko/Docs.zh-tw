---
title: "支援多重 IIS 網站繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ebe433d1c18d46e0868f9566a273124e6bd63f1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="supporting-multiple-iis-site-bindings"></a><span data-ttu-id="e2b6a-102">支援多重 IIS 網站繫結</span><span class="sxs-lookup"><span data-stu-id="e2b6a-102">Supporting Multiple IIS Site Bindings</span></span>
<span data-ttu-id="e2b6a-103">在網際網路資訊服務 (IIS) 7.0 之下裝載 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時，您可能需要提供在相同網站使用相同通訊協定的多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) 7.0, you may want to provide multiple base addresses that use the same protocol on the same site.</span></span> <span data-ttu-id="e2b6a-104">這樣可讓相同的服務回應數個不同的 URI。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-104">This allows the same service to respond to a number of different URIs.</span></span> <span data-ttu-id="e2b6a-105">當您要裝載在 http://www.contoso.com 和 http://contoso.com 接聽的服務時，這種方式就會很有用。當您所建立的服務具有內部使用者基底位址，同時具有外部使用者個別基底位址時，也適用此方式。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-105">This is useful when you want to host a service that listens on http://www.contoso.com and http://contoso.com. It is also useful to create a service that has a base address for internal users and a separate base address for external users.</span></span> <span data-ttu-id="e2b6a-106">例如：http://internal.contoso.com 和 http://www.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-106">For example: http://internal.contoso.com and http://www.contoso.com.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2b6a-107">不過這個功能僅適用於 HTTP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-107">This functionality is only available using the HTTP protocol.</span></span>  
  
## <a name="multiple-base-addresses"></a><span data-ttu-id="e2b6a-108">多個基底位址</span><span class="sxs-lookup"><span data-stu-id="e2b6a-108">Multiple Base Addresses</span></span>  
 <span data-ttu-id="e2b6a-109">只有在 IIS 之下裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務才能使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-109">This feature is only available to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services that are hosted under IIS.</span></span> <span data-ttu-id="e2b6a-110">預設不會啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-110">This feature is not enabled by default.</span></span> <span data-ttu-id="e2b6a-111">若要啟用它，您必須加入`multipleSiteBindingsEnabled`屬性加入 <`serviceHostingEnvironment`> 在 Web.config 中的項目檔案，並將它設定為`true`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-111">To enable it you must add the `multipleSiteBindingsEnabled` attribute to the <`serviceHostingEnvironment`> element in your Web.config file and set it to `true`, as shown in the following example.</span></span>  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 <span data-ttu-id="e2b6a-112">在 IIS 之下裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，IIS 會根據 URI 建立一個基底位址，並加入至含有應用程式的虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-112">When hosting a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under IIS, IIS creates one base address for you based on the URI to the virtual directory that contains the application.</span></span> <span data-ttu-id="e2b6a-113">您可以使用 Internet Information Services 管理員，加入其他使用相同通訊協定的基底位址，以便在網站中加入一個或多個繫結。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-113">You can add additional base addresses that use the same protocol by using Internet Information Services Manager to add one or more bindings to your Web site.</span></span> <span data-ttu-id="e2b6a-114">為每個繫結指定通訊協定 (HTTP 或 HTTPS)、IP 位址、連接埠和主機名稱。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-114">For each binding specify a protocol (HTTP or HTTPS), an IP address, a port, and a host name.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e2b6a-115">使用 Internet Information Services 管理員，請參閱[IIS 管理員 (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057)。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-115"> using Internet Information Services Manager, see [IIS Manager (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e2b6a-116">加入繫結至站台，請參閱[建立網站 (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)</span><span class="sxs-lookup"><span data-stu-id="e2b6a-116"> adding bindings to a site, see [Create a Web Site (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)</span></span>  
  
 <span data-ttu-id="e2b6a-117">為相同網站指定多個基底位址會影響 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [說明] 頁面的內容、匯入結構描述，以及由服務所產生的 WSDL/MEX 資訊。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-117">Specifying multiple base addresses for the same site affects the content of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Help page, importing schema, and the WSDL/MEX information generated by the service.</span></span> <span data-ttu-id="e2b6a-118">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [說明] 頁面會顯示命令列，可用於產生與服務進行通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-118">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Help page displays the command line to use to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that can communicate with the service.</span></span> <span data-ttu-id="e2b6a-119">此命令列僅包含在 IIS 繫結中指定的第一個網站位址。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-119">This command line contains only the first address specified in the IIS binding for the Web site.</span></span> <span data-ttu-id="e2b6a-120">同樣地，在匯入結構時，只會使用在 IIS 繫結中指定的第一個基底位址。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-120">Similarly when importing schema, only the first base address specified in the IIS binding is used.</span></span> <span data-ttu-id="e2b6a-121">WSDL 和 MEX 資料包含所有在 IIS 繫結中指定的基底位址。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-121">WSDL and MEX data contain all the base addresses specified in the IIS bindings.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="e2b6a-122">這表示如果服務擁有兩個基底位址，一個用於內部使用者，另一個用於外部使用者，則會在由服務所產生的 WSDL/MEX 資訊中指定這兩個位址。</span><span class="sxs-lookup"><span data-stu-id="e2b6a-122">This means that if a service has two base addresses, one for internal users and one for external users, both are specified in the WSDL/MEX information generated by the service.</span></span>
