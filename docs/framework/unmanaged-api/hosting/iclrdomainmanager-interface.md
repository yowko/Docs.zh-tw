---
title: ICLRDomainManager 介面
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: aa874205cf14232e7a69ed2215086e33c0beab4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129346"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="70822-102">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="70822-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="70822-103">可讓主機指定將用來初始化預設應用程式域的應用程式網域管理員，以及指定初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="70822-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70822-104">方法</span><span class="sxs-lookup"><span data-stu-id="70822-104">Methods</span></span>  
  
|<span data-ttu-id="70822-105">方法</span><span class="sxs-lookup"><span data-stu-id="70822-105">Method</span></span>|<span data-ttu-id="70822-106">描述</span><span class="sxs-lookup"><span data-stu-id="70822-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70822-107">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="70822-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="70822-108">指定將用來初始化預設應用程式域之應用程式網域管理員的衍生自 <xref:System.AppDomainManager?displayProperty=nameWithType> 類別的型別。</span><span class="sxs-lookup"><span data-stu-id="70822-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="70822-109">SetPropertiesForDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="70822-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="70822-110">設定將用來初始化預設應用程式域的屬性。</span><span class="sxs-lookup"><span data-stu-id="70822-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70822-111">備註</span><span class="sxs-lookup"><span data-stu-id="70822-111">Remarks</span></span>  
 <span data-ttu-id="70822-112">若要取得此介面的實例，請呼叫[ICLRControl：： GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法，並以 MANAGER 類型 IID `IID_ICLRDomainManager`。</span><span class="sxs-lookup"><span data-stu-id="70822-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70822-113">需求</span><span class="sxs-lookup"><span data-stu-id="70822-113">Requirements</span></span>  
 <span data-ttu-id="70822-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70822-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70822-115">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="70822-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="70822-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="70822-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70822-117">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70822-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70822-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="70822-118">See also</span></span>

- [<span data-ttu-id="70822-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="70822-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="70822-120">裝載</span><span class="sxs-lookup"><span data-stu-id="70822-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
