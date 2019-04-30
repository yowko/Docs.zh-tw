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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970023"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="ab8a5-102">IAppDomainSetup 介面</span><span class="sxs-lookup"><span data-stu-id="ab8a5-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="ab8a5-103">提供可讓主應用程式設定的屬性<xref:System.AppDomain?displayProperty=nameWithType>型別之前呼叫[icorruntimehost:: Createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法用來建立它。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab8a5-104">屬性</span><span class="sxs-lookup"><span data-stu-id="ab8a5-104">Properties</span></span>  
  
|<span data-ttu-id="ab8a5-105">屬性</span><span class="sxs-lookup"><span data-stu-id="ab8a5-105">Property</span></span>|<span data-ttu-id="ab8a5-106">描述</span><span class="sxs-lookup"><span data-stu-id="ab8a5-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="ab8a5-107">取得或設定包含應用程式目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="ab8a5-108">取得或設定應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="ab8a5-109">取得或設定其中的檔案已陰影複製的應用程式特定區域的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="ab8a5-110">取得或設定應用程式的組態檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="ab8a5-111">取得或設定儲存及存取動態產生的檔案的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="ab8a5-112">取得或設定與此網域相關聯的授權檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="ab8a5-113">取得或設定結合的目錄清單<xref:System.AppDomainSetup.ApplicationBase%2A>探查私用組件的目錄。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="ab8a5-114">取得或設定字串值，包含或排除<xref:System.AppDomainSetup.ApplicationBase%2A>從應用程式的搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="ab8a5-115">取得或設定包含要陰影複製組件目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="ab8a5-116">取得或設定字串，表示陰影複製開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="ab8a5-117">有效值為"true"或"false"。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab8a5-118">備註</span><span class="sxs-lookup"><span data-stu-id="ab8a5-118">Remarks</span></span>  
 <span data-ttu-id="ab8a5-119">`IAppDomainSetup`介面會對應至 managed<xref:System.IAppDomainSetup>介面，其中<xref:System.AppDomainSetup>型別會實作。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="ab8a5-120">請參閱<xref:System.IAppDomainSetup?displayProperty=nameWithType>如其屬性的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="ab8a5-121">`IAppDomainSetup` 表示可以加入的組件繫結資訊<xref:System.AppDomain>之前建立的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="ab8a5-122">例如，主機可以設定<xref:System.AppDomainSetup.ApplicationBase%2A>屬性，以建立根目錄，common language runtime (CLR) 探查 managed 組件。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab8a5-123">需求</span><span class="sxs-lookup"><span data-stu-id="ab8a5-123">Requirements</span></span>  
 <span data-ttu-id="ab8a5-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab8a5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab8a5-125">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ab8a5-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab8a5-126">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ab8a5-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab8a5-127">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab8a5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8a5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab8a5-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="ab8a5-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ab8a5-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
