---
title: "ICLRDomainManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager
helpviewer_keywords: ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75a7e93d26a5c77484d78ad4632bedf8def6a44b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="0359a-102">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="0359a-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="0359a-103">可讓主應用程式指定將用於初始化預設應用程式定義域，並指定初始化屬性的應用程式定義域管理員。</span><span class="sxs-lookup"><span data-stu-id="0359a-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0359a-104">方法</span><span class="sxs-lookup"><span data-stu-id="0359a-104">Methods</span></span>  
  
|<span data-ttu-id="0359a-105">方法</span><span class="sxs-lookup"><span data-stu-id="0359a-105">Method</span></span>|<span data-ttu-id="0359a-106">說明</span><span class="sxs-lookup"><span data-stu-id="0359a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0359a-107">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="0359a-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="0359a-108">指定型別，衍生自<xref:System.AppDomainManager?displayProperty=nameWithType>類別，將會用來初始化預設應用程式定義域的應用程式定義域管理員。</span><span class="sxs-lookup"><span data-stu-id="0359a-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="0359a-109">SetPropertiesForDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="0359a-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="0359a-110">設定將用來初始化預設應用程式定義域的屬性。</span><span class="sxs-lookup"><span data-stu-id="0359a-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0359a-111">備註</span><span class="sxs-lookup"><span data-stu-id="0359a-111">Remarks</span></span>  
 <span data-ttu-id="0359a-112">若要取得此介面的執行個體，請呼叫[iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)管理員型別 IID 方法`IID_ICLRDomainManager`。</span><span class="sxs-lookup"><span data-stu-id="0359a-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0359a-113">需求</span><span class="sxs-lookup"><span data-stu-id="0359a-113">Requirements</span></span>  
 <span data-ttu-id="0359a-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0359a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0359a-115">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0359a-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0359a-116">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0359a-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0359a-117">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0359a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0359a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0359a-118">See Also</span></span>  
 [<span data-ttu-id="0359a-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="0359a-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="0359a-120">裝載</span><span class="sxs-lookup"><span data-stu-id="0359a-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
