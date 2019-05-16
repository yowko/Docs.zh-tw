---
title: 在 IIS 與 WAS 中以組態為基礎的啟動
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 99f6c7d41620a7bafea0981cbeaa5cdcbad5ef12
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636131"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="d207a-102">在 IIS 與 WAS 中以組態為基礎的啟動</span><span class="sxs-lookup"><span data-stu-id="d207a-102">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="d207a-103">通常當裝載在 Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 下的 Windows Communication Foundation (WCF) 服務，您必須提供.svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="d207a-103">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="d207a-104">.svc 檔案包含服務名稱和選擇性自訂服務主機處理站。</span><span class="sxs-lookup"><span data-stu-id="d207a-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="d207a-105">此額外的檔案會增加管理能力的負荷。</span><span class="sxs-lookup"><span data-stu-id="d207a-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="d207a-106">以組態為基礎的啟動功能可免除 .svc 檔案的需求以及關聯的負荷。</span><span class="sxs-lookup"><span data-stu-id="d207a-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="d207a-107">以組態為基礎的啟用</span><span class="sxs-lookup"><span data-stu-id="d207a-107">Configuration-Based Activation</span></span>

<span data-ttu-id="d207a-108">以組態為基礎的啟動會使用放置於 .svc 檔案中的中繼資料，並將中繼資料放置於 Web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="d207a-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="d207a-109">在 <`serviceHostingEnvironment`> 元素沒有 <`serviceActivations`> 項目。</span><span class="sxs-lookup"><span data-stu-id="d207a-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="d207a-110">在 <`serviceActivations`> 項目是否有一或多個 <`add`> 項目，一個用於每個託管服務。</span><span class="sxs-lookup"><span data-stu-id="d207a-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="d207a-111"><`add`> 元素包含可讓您設定服務和服務類型或服務主機處理站的相對位址的屬性。</span><span class="sxs-lookup"><span data-stu-id="d207a-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="d207a-112">下列組態範例程式碼會示範此區段的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d207a-112">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
>  <span data-ttu-id="d207a-113">每個 <`add`> 項目必須指定服務或處理站屬性。</span><span class="sxs-lookup"><span data-stu-id="d207a-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="d207a-114">系統允許同時指定服務和處理站屬性。</span><span class="sxs-lookup"><span data-stu-id="d207a-114">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="d207a-115">如果 Web.config 檔案具有這項設定，您就可以將服務原始程式碼放置於應用程式的 App_Code 目錄中，或者將已編譯的組件放置於應用程式的 Bin 目錄中。</span><span class="sxs-lookup"><span data-stu-id="d207a-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
> - <span data-ttu-id="d207a-116">使用以組態為基礎的啟動時，不支援 .svc 檔案中的內嵌程式碼。</span><span class="sxs-lookup"><span data-stu-id="d207a-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="d207a-117">`relativeAddress`屬性必須設為相對位址這類 「\<子目錄 > / service.svc"或"~ /\<子 sub-directory/service.svc"。</span><span class="sxs-lookup"><span data-stu-id="d207a-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="d207a-118">如果您註冊未包含與 WCF 關聯之已知副檔名的相對位址，便會擲回組態例外。</span><span class="sxs-lookup"><span data-stu-id="d207a-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="d207a-119">指定的相對位址與虛擬應用程式的根相關。</span><span class="sxs-lookup"><span data-stu-id="d207a-119">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="d207a-120">由於組態模型為階層式，主機上註冊的相對位址和網站層級會由虛擬應用程式繼承。</span><span class="sxs-lookup"><span data-stu-id="d207a-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="d207a-121">在組態檔中的註冊優先權高於 .svc、.xamlx、.xoml 或其他檔案中的設定。</span><span class="sxs-lookup"><span data-stu-id="d207a-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="d207a-122">任何在 URI 中傳送至 IIS/WAS 的 ‘\’ (反斜線) 會自動轉換為 ‘/’ (正斜線)。</span><span class="sxs-lookup"><span data-stu-id="d207a-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="d207a-123">如果新增包含 ‘\’ 的相對位址且您傳送使用相對位址的 URI 至 IIS，反斜線會轉換為正斜線，而 IIS 無法將其與相對位址比對。</span><span class="sxs-lookup"><span data-stu-id="d207a-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="d207a-124">IIS 會送出追蹤資訊，表示找不到相符的項目。</span><span class="sxs-lookup"><span data-stu-id="d207a-124">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="d207a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d207a-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="d207a-126">裝載服務</span><span class="sxs-lookup"><span data-stu-id="d207a-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="d207a-127">裝載工作流程服務概觀</span><span class="sxs-lookup"><span data-stu-id="d207a-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [<span data-ttu-id="d207a-128">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="d207a-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [<span data-ttu-id="d207a-129">Windows Server AppFabric 裝載功能</span><span class="sxs-lookup"><span data-stu-id="d207a-129">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
