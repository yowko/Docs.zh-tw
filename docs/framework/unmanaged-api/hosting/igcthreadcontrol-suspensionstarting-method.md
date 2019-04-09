---
title: IGCThreadControl::SuspensionStarting 方法
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7613bc744ad4c2e172fc4f6dd7bf282fb3d9072c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179747"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="4b7e7-102">IGCThreadControl::SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="4b7e7-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="4b7e7-103">通知記憶體回收執行緒暫止或其他暫停，正在開始執行階段主應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b7e7-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b7e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b7e7-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b7e7-105">備註</span><span class="sxs-lookup"><span data-stu-id="4b7e7-105">Remarks</span></span>  
 <span data-ttu-id="4b7e7-106">請勿重新排程在任何執行緒`SuspensionStarting`回呼。</span><span class="sxs-lookup"><span data-stu-id="4b7e7-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b7e7-107">需求</span><span class="sxs-lookup"><span data-stu-id="4b7e7-107">Requirements</span></span>  
 <span data-ttu-id="4b7e7-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b7e7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b7e7-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b7e7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b7e7-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4b7e7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4b7e7-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="4b7e7-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b7e7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b7e7-112">See also</span></span>

- [<span data-ttu-id="4b7e7-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="4b7e7-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
