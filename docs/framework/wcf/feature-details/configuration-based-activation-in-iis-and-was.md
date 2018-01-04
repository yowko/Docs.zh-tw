---
title: "在 IIS 與 WAS 中以組態為基礎的啟動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc0e954ae5cadbe7e70cd8a83d3d5841f4e0d142
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="2c24f-102">在 IIS 與 WAS 中以組態為基礎的啟動</span><span class="sxs-lookup"><span data-stu-id="2c24f-102">Configuration-Based Activation in IIS and WAS</span></span>
<span data-ttu-id="2c24f-103">一般來說，在 Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 底下裝載 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時，您必須提供 .svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="2c24f-103">Normally when hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="2c24f-104">.svc 檔案包含服務名稱和選擇性自訂服務主機處理站。</span><span class="sxs-lookup"><span data-stu-id="2c24f-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="2c24f-105">此額外的檔案會增加管理能力的負荷。</span><span class="sxs-lookup"><span data-stu-id="2c24f-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="2c24f-106">以組態為基礎的啟動功能可免除 .svc 檔案的需求以及關聯的負荷。</span><span class="sxs-lookup"><span data-stu-id="2c24f-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>  
  
## <a name="configuration-based-activation"></a><span data-ttu-id="2c24f-107">以組態為基礎的啟用</span><span class="sxs-lookup"><span data-stu-id="2c24f-107">Configuration-Based Activation</span></span>  
 <span data-ttu-id="2c24f-108">以組態為基礎的啟動會使用放置於 .svc 檔案中的中繼資料，並將中繼資料放置於 Web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="2c24f-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="2c24f-109">在 <`serviceHostingEnvironment`> 元素沒有 <`serviceActivations`> 項目。</span><span class="sxs-lookup"><span data-stu-id="2c24f-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="2c24f-110">在 <`serviceActivations`> 項目是一或多個 <`add`> 項目、 一個用於每個託管服務。</span><span class="sxs-lookup"><span data-stu-id="2c24f-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="2c24f-111"><`add`> 元素包含可讓您設定服務和服務類型或服務主機處理站的相對位址的屬性。</span><span class="sxs-lookup"><span data-stu-id="2c24f-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="2c24f-112">下列組態範例程式碼會示範此區段的使用方式。</span><span class="sxs-lookup"><span data-stu-id="2c24f-112">The following configuration example code shows how this section is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c24f-113">每個 <`add`> 項目必須指定服務或處理站屬性。</span><span class="sxs-lookup"><span data-stu-id="2c24f-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="2c24f-114">系統允許同時指定服務和處理站屬性。</span><span class="sxs-lookup"><span data-stu-id="2c24f-114">Specifying both service and factory attributes is allowed.</span></span>  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 <span data-ttu-id="2c24f-115">如果 Web.config 檔案具有這項設定，您就可以將服務原始程式碼放置於應用程式的 App_Code 目錄中，或者將已編譯的組件放置於應用程式的 Bin 目錄中。</span><span class="sxs-lookup"><span data-stu-id="2c24f-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="2c24f-116">使用以組態為基礎的啟動時，不支援 .svc 檔案中的內嵌程式碼。</span><span class="sxs-lookup"><span data-stu-id="2c24f-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>  
> -   <span data-ttu-id="2c24f-117">`relativeAddress`屬性必須設定為相對位址例如"\<子目錄 > / service.svc"或"~ /\<子-/<sub-directory/service.svc"。</span><span class="sxs-lookup"><span data-stu-id="2c24f-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>  
> -   <span data-ttu-id="2c24f-118">如果您註冊未包含與 WCF 關聯之已知副檔名的相對位址，便會擲回組態例外。</span><span class="sxs-lookup"><span data-stu-id="2c24f-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>  
> -   <span data-ttu-id="2c24f-119">指定的相對位址與虛擬應用程式的根相關。</span><span class="sxs-lookup"><span data-stu-id="2c24f-119">The relative address specified is relative to the root of the virtual application.</span></span>  
> -   <span data-ttu-id="2c24f-120">由於組態模型為階層式，主機上註冊的相對位址和網站層級會由虛擬應用程式繼承。</span><span class="sxs-lookup"><span data-stu-id="2c24f-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>  
> -   <span data-ttu-id="2c24f-121">在組態檔中的註冊優先權高於 .svc、.xamlx、.xoml 或其他檔案中的設定。</span><span class="sxs-lookup"><span data-stu-id="2c24f-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>  
> -   <span data-ttu-id="2c24f-122">任何在 URI 中傳送至 IIS/WAS 的 ‘\’ (反斜線) 會自動轉換為 ‘/’ (正斜線)。</span><span class="sxs-lookup"><span data-stu-id="2c24f-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="2c24f-123">如果新增包含 ‘\’ 的相對位址且您傳送使用相對位址的 URI 至 IIS，反斜線會轉換為正斜線，而 IIS 無法將其與相對位址比對。</span><span class="sxs-lookup"><span data-stu-id="2c24f-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="2c24f-124">IIS 會送出追蹤資訊，表示找不到相符的項目。</span><span class="sxs-lookup"><span data-stu-id="2c24f-124">IIS sends out trace information that indicates that there are no matches found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c24f-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c24f-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [<span data-ttu-id="2c24f-126">裝載服務</span><span class="sxs-lookup"><span data-stu-id="2c24f-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="2c24f-127">裝載工作流程服務概觀</span><span class="sxs-lookup"><span data-stu-id="2c24f-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [<span data-ttu-id="2c24f-128">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="2c24f-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [<span data-ttu-id="2c24f-129">Windows Server App Fabric 裝載功能</span><span class="sxs-lookup"><span data-stu-id="2c24f-129">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
