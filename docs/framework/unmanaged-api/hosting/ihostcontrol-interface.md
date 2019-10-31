---
title: IHostControl 介面
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 444a78705c61d5a53764f55185ef1a907830bd71
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195875"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="742bb-102">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="742bb-102">IHostControl Interface</span></span>
<span data-ttu-id="742bb-103">提供設定元件載入的方法，以及判斷主機支援的主控介面。</span><span class="sxs-lookup"><span data-stu-id="742bb-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="742bb-104">方法</span><span class="sxs-lookup"><span data-stu-id="742bb-104">Methods</span></span>  
  
|<span data-ttu-id="742bb-105">方法</span><span class="sxs-lookup"><span data-stu-id="742bb-105">Method</span></span>|<span data-ttu-id="742bb-106">描述</span><span class="sxs-lookup"><span data-stu-id="742bb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="742bb-107">GetHostManager 方法</span><span class="sxs-lookup"><span data-stu-id="742bb-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="742bb-108">取得具有指定 `IID`之介面的主機介面指標。</span><span class="sxs-lookup"><span data-stu-id="742bb-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="742bb-109">SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="742bb-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="742bb-110">通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="742bb-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="742bb-111">需求</span><span class="sxs-lookup"><span data-stu-id="742bb-111">Requirements</span></span>  
 <span data-ttu-id="742bb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="742bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="742bb-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="742bb-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="742bb-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="742bb-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="742bb-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="742bb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742bb-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="742bb-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="742bb-117">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="742bb-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="742bb-118">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="742bb-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="742bb-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="742bb-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
