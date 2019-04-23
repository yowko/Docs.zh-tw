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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179747"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="d0ab0-102">IGCThreadControl::SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="d0ab0-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="d0ab0-103">通知記憶體回收執行緒暫止或其他暫停，正在開始執行階段主應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0ab0-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ab0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0ab0-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="d0ab0-105">備註</span><span class="sxs-lookup"><span data-stu-id="d0ab0-105">Remarks</span></span>  
 <span data-ttu-id="d0ab0-106">請勿重新排程在任何執行緒`SuspensionStarting`回呼。</span><span class="sxs-lookup"><span data-stu-id="d0ab0-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ab0-107">需求</span><span class="sxs-lookup"><span data-stu-id="d0ab0-107">Requirements</span></span>  
 <span data-ttu-id="d0ab0-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0ab0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0ab0-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0ab0-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0ab0-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d0ab0-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0ab0-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ab0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ab0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0ab0-112">See also</span></span>

- [<span data-ttu-id="d0ab0-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="d0ab0-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
