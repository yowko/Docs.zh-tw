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
ms.openlocfilehash: ff0c95ea79978c0b58057ec06fea231f5632c941
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702648"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="b4a94-102">IGCThreadControl::SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="b4a94-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="b4a94-103">通知記憶體回收執行緒暫止或其他暫停，正在開始執行階段主應用程式。</span><span class="sxs-lookup"><span data-stu-id="b4a94-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a94-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4a94-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b4a94-105">備註</span><span class="sxs-lookup"><span data-stu-id="b4a94-105">Remarks</span></span>  
 <span data-ttu-id="b4a94-106">請勿重新排程在任何執行緒`SuspensionStarting`回呼。</span><span class="sxs-lookup"><span data-stu-id="b4a94-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4a94-107">需求</span><span class="sxs-lookup"><span data-stu-id="b4a94-107">Requirements</span></span>  
 <span data-ttu-id="b4a94-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4a94-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4a94-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4a94-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4a94-110">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b4a94-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4a94-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4a94-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a94-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4a94-112">See also</span></span>
- [<span data-ttu-id="b4a94-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="b4a94-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
