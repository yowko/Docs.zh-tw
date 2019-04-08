---
title: IGCHost::SetVirtualMemLimit 方法
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5b4210bda7d41b190f1025b62132c5df896a2a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088388"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="ef04f-102">IGCHost::SetVirtualMemLimit 方法</span><span class="sxs-lookup"><span data-stu-id="ef04f-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="ef04f-103">設定執行階段的虛擬記憶體的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ef04f-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef04f-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef04f-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef04f-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef04f-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="ef04f-106">[in]最大大小 （mb），執行階段的虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="ef04f-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef04f-107">備註</span><span class="sxs-lookup"><span data-stu-id="ef04f-107">Remarks</span></span>  
 <span data-ttu-id="ef04f-108">執行階段的虛擬記憶體大小上限可以動態變更。</span><span class="sxs-lookup"><span data-stu-id="ef04f-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef04f-109">需求</span><span class="sxs-lookup"><span data-stu-id="ef04f-109">Requirements</span></span>  
 <span data-ttu-id="ef04f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef04f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef04f-111">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="ef04f-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ef04f-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ef04f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ef04f-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ef04f-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef04f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef04f-114">See also</span></span>

- [<span data-ttu-id="ef04f-115">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="ef04f-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
