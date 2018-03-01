---
title: "ICorPublishProcess::EnumAppDomains 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 938c022788d5ed9f0e28f794432017748dc096e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="434e9-102">ICorPublishProcess::EnumAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="434e9-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="434e9-103">取得應用程式定義域所參考的這個程序中的列舉值[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="434e9-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="434e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="434e9-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="434e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="434e9-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="434e9-106">[out]位址指標[ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)允許逐一查看集合的應用程式定義域，在此程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="434e9-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="434e9-107">備註</span><span class="sxs-lookup"><span data-stu-id="434e9-107">Remarks</span></span>  
 <span data-ttu-id="434e9-108">應用程式定義域的清單為基礎的應用程式定義域存在的快照集時`EnumAppDomains`方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="434e9-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="434e9-109">若要建立新的最新清單可能會多次呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="434e9-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="434e9-110">這個方法的後續呼叫將不會影響現有的清單。</span><span class="sxs-lookup"><span data-stu-id="434e9-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="434e9-111">如果處理序已終止， `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED HRESULT 值將會失敗。</span><span class="sxs-lookup"><span data-stu-id="434e9-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="434e9-112">需求</span><span class="sxs-lookup"><span data-stu-id="434e9-112">Requirements</span></span>  
 <span data-ttu-id="434e9-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="434e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="434e9-114">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="434e9-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="434e9-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="434e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="434e9-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="434e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434e9-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="434e9-117">See Also</span></span>  
 [<span data-ttu-id="434e9-118">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="434e9-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
