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
ms.openlocfilehash: d504101747995557ba526c88de451ebab7b3c556
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698549"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="23b15-102">IAppDomainSetup 介面</span><span class="sxs-lookup"><span data-stu-id="23b15-102">IAppDomainSetup Interface</span></span>

<span data-ttu-id="23b15-103">提供屬性，可讓主機在 <xref:System.AppDomain?displayProperty=nameWithType> 呼叫 [ICorRuntimeHost：： CreateDomainEx](icorruntimehost-createdomainex-method.md) 方法來建立類型之前，先設定類型。</span><span class="sxs-lookup"><span data-stu-id="23b15-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="23b15-104">屬性</span><span class="sxs-lookup"><span data-stu-id="23b15-104">Properties</span></span>  
  
|<span data-ttu-id="23b15-105">屬性</span><span class="sxs-lookup"><span data-stu-id="23b15-105">Property</span></span>|<span data-ttu-id="23b15-106">描述</span><span class="sxs-lookup"><span data-stu-id="23b15-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="23b15-107">取得或設定包含應用程式的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="23b15-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="23b15-108">取得或設定應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="23b15-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="23b15-109">取得或設定應用程式特定區域的名稱，其中檔案會以陰影複製。</span><span class="sxs-lookup"><span data-stu-id="23b15-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="23b15-110">取得或設定應用程式的設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="23b15-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="23b15-111">取得或設定用來儲存和存取動態產生之檔案的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="23b15-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="23b15-112">取得或設定與此網域相關聯之授權檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="23b15-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="23b15-113">取得或設定目錄的清單，這些目錄會與 <xref:System.AppDomainSetup.ApplicationBase%2A> 要探查私用元件的目錄合併。</span><span class="sxs-lookup"><span data-stu-id="23b15-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="23b15-114">取得或設定字串值，這個值會在 <xref:System.AppDomainSetup.ApplicationBase%2A> 應用程式的搜尋路徑中加入或排除。</span><span class="sxs-lookup"><span data-stu-id="23b15-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="23b15-115">取得或設定包含要陰影複製之元件的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="23b15-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="23b15-116">取得或設定字串，這個字串表示是否開啟或關閉陰影複製。</span><span class="sxs-lookup"><span data-stu-id="23b15-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="23b15-117">有效的值為 "true" 或 "false"。</span><span class="sxs-lookup"><span data-stu-id="23b15-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b15-118">備註</span><span class="sxs-lookup"><span data-stu-id="23b15-118">Remarks</span></span>  

 <span data-ttu-id="23b15-119">`IAppDomainSetup`介面會對應至型別所實的 managed <xref:System.IAppDomainSetup> 介面 <xref:System.AppDomainSetup> 。</span><span class="sxs-lookup"><span data-stu-id="23b15-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="23b15-120"><xref:System.IAppDomainSetup?displayProperty=nameWithType>如需其屬性的詳細描述，請參閱。</span><span class="sxs-lookup"><span data-stu-id="23b15-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="23b15-121">`IAppDomainSetup` 表示元件系結資訊，可以 <xref:System.AppDomain> 在實例建立之前將其加入至實例。</span><span class="sxs-lookup"><span data-stu-id="23b15-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="23b15-122">例如，主機可以設定 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性來建立根目錄，而 common language runtime (CLR) 探查 managed 元件。</span><span class="sxs-lookup"><span data-stu-id="23b15-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23b15-123">需求</span><span class="sxs-lookup"><span data-stu-id="23b15-123">Requirements</span></span>  

 <span data-ttu-id="23b15-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23b15-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b15-125">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="23b15-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23b15-126">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="23b15-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23b15-127">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b15-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b15-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23b15-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="23b15-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="23b15-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
