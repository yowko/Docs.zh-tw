---
title: IAppDomainSetup 介面
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126865"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="5c2dd-102">IAppDomainSetup 介面</span><span class="sxs-lookup"><span data-stu-id="5c2dd-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="5c2dd-103">提供可讓主機設定 <xref:System.AppDomain?displayProperty=nameWithType> 類型的屬性，然後再呼叫[ICorRuntimeHost：： CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法來建立它。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5c2dd-104">內容</span><span class="sxs-lookup"><span data-stu-id="5c2dd-104">Properties</span></span>  
  
|<span data-ttu-id="5c2dd-105">屬性</span><span class="sxs-lookup"><span data-stu-id="5c2dd-105">Property</span></span>|<span data-ttu-id="5c2dd-106">描述</span><span class="sxs-lookup"><span data-stu-id="5c2dd-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="5c2dd-107">取得或設定包含應用程式的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="5c2dd-108">取得或設定應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="5c2dd-109">取得或設定應用程式特定的區功能變數名稱稱，其中會遮蔽檔案的陰影複製位置。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="5c2dd-110">取得或設定應用程式的設定檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="5c2dd-111">取得或設定用來儲存和存取動態產生的檔案之目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="5c2dd-112">取得或設定與此網域相關聯之授權檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="5c2dd-113">取得或設定與 <xref:System.AppDomainSetup.ApplicationBase%2A> 目錄結合的目錄清單，以探查私用元件。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="5c2dd-114">取得或設定字串值，其中包含或排除來自應用程式搜尋路徑的 <xref:System.AppDomainSetup.ApplicationBase%2A>。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="5c2dd-115">取得或設定包含要陰影複製之元件的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="5c2dd-116">取得或設定字串，指出陰影複製是否開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="5c2dd-117">有效的值為 "true" 或 "false"。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c2dd-118">備註</span><span class="sxs-lookup"><span data-stu-id="5c2dd-118">Remarks</span></span>  
 <span data-ttu-id="5c2dd-119">`IAppDomainSetup` 介面會對應到 <xref:System.AppDomainSetup> 類型所執行的 managed <xref:System.IAppDomainSetup> 介面。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="5c2dd-120">如需其屬性的詳細說明，請參閱 <xref:System.IAppDomainSetup?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="5c2dd-121">`IAppDomainSetup` 代表元件系結資訊，可以在建立之前加入至 <xref:System.AppDomain> 實例。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="5c2dd-122">例如，主控制項可以設定 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性，以建立根目錄，而 common language runtime （CLR）會探查 managed 元件。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c2dd-123">需求</span><span class="sxs-lookup"><span data-stu-id="5c2dd-123">Requirements</span></span>  
 <span data-ttu-id="5c2dd-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c2dd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c2dd-125">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5c2dd-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c2dd-126">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5c2dd-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c2dd-127">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c2dd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c2dd-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c2dd-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="5c2dd-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="5c2dd-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
