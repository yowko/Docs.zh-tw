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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 014e5c9951091046ae07374794743e82affcd5ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967724"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="8f56f-102">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="8f56f-102">IHostControl Interface</span></span>
<span data-ttu-id="8f56f-103">提供對於設定載入的組件，以及判斷哪些裝載介面主應用程式支援的方法。</span><span class="sxs-lookup"><span data-stu-id="8f56f-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f56f-104">方法</span><span class="sxs-lookup"><span data-stu-id="8f56f-104">Methods</span></span>  
  
|<span data-ttu-id="8f56f-105">方法</span><span class="sxs-lookup"><span data-stu-id="8f56f-105">Method</span></span>|<span data-ttu-id="8f56f-106">描述</span><span class="sxs-lookup"><span data-stu-id="8f56f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f56f-107">GetHostManager 方法</span><span class="sxs-lookup"><span data-stu-id="8f56f-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="8f56f-108">取得主機的介面實作的介面指標，具有指定`IID`。</span><span class="sxs-lookup"><span data-stu-id="8f56f-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="8f56f-109">SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="8f56f-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="8f56f-110">主應用程式已建立的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="8f56f-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f56f-111">需求</span><span class="sxs-lookup"><span data-stu-id="8f56f-111">Requirements</span></span>  
 <span data-ttu-id="8f56f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f56f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f56f-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f56f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f56f-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8f56f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f56f-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f56f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f56f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f56f-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="8f56f-117">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="8f56f-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="8f56f-118">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="8f56f-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="8f56f-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="8f56f-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
