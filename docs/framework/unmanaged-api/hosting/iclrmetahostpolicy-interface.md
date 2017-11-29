---
title: "ICLRMetaHostPolicy 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b8cbe1d397e1214cfa4d3f4cbc3d6cdf2d3ccd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="f2836-102">ICLRMetaHostPolicy 介面</span><span class="sxs-lookup"><span data-stu-id="f2836-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="f2836-103">提供[GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法，讓指標回到通用的 language runtime (CLR) 介面，根據原則的條件，管理組件、 版本和組態檔。</span><span class="sxs-lookup"><span data-stu-id="f2836-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2836-104">方法</span><span class="sxs-lookup"><span data-stu-id="f2836-104">Methods</span></span>  
  
|<span data-ttu-id="f2836-105">方法</span><span class="sxs-lookup"><span data-stu-id="f2836-105">Method</span></span>|<span data-ttu-id="f2836-106">說明</span><span class="sxs-lookup"><span data-stu-id="f2836-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2836-107">GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="f2836-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="f2836-108">提供的慣用的 CLR 介面根據原則的條件，管理組件、 版本和組態檔。</span><span class="sxs-lookup"><span data-stu-id="f2836-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2836-109">備註</span><span class="sxs-lookup"><span data-stu-id="f2836-109">Remarks</span></span>  
 <span data-ttu-id="f2836-110">您可以取得此介面的參考，藉由呼叫[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="f2836-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="f2836-111">這個介面不實際上不會載入或啟用 CLR，但只會傳回可用的版本會安裝或載入為基礎的慣用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="f2836-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="f2836-112">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]裝載 API，將合併原則，讓主機有特定的需求可能會使用基本功能而不會產生非預期的負面影響。</span><span class="sxs-lookup"><span data-stu-id="f2836-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="f2836-113">例如，許多 MSCorEE.dll 匯出會繫結至特定的 CLR，雖然方法可能會以邏輯方式需要它。</span><span class="sxs-lookup"><span data-stu-id="f2836-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="f2836-114">[METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)列舉型別提供通用於大多數的主控件的繫結原則。</span><span class="sxs-lookup"><span data-stu-id="f2836-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2836-115">需求</span><span class="sxs-lookup"><span data-stu-id="f2836-115">Requirements</span></span>  
 <span data-ttu-id="f2836-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2836-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2836-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f2836-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f2836-118">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f2836-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2836-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2836-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2836-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2836-120">See Also</span></span>  
 [<span data-ttu-id="f2836-121">在.NET Framework 4 和 4.5 加入的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="f2836-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="f2836-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="f2836-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f2836-123">裝載</span><span class="sxs-lookup"><span data-stu-id="f2836-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
