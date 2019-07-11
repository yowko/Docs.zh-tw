---
title: ICorPublishProcess::EnumAppDomains 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c614afee18824e1672b378dd468cb11c9c173d9f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764955"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="3b3ed-102">ICorPublishProcess::EnumAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="3b3ed-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="3b3ed-103">取得列舉值所參考的處理序中的應用程式定義域[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="3b3ed-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b3ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b3ed-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b3ed-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b3ed-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="3b3ed-106">[out]位址指標[ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)允許逐一查看集合的應用程式定義域，在此程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3b3ed-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b3ed-107">備註</span><span class="sxs-lookup"><span data-stu-id="3b3ed-107">Remarks</span></span>  
 <span data-ttu-id="3b3ed-108">應用程式定義域的清單為基礎的應用程式定義域存在的快照集時`EnumAppDomains`呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="3b3ed-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="3b3ed-109">可能會多次呼叫這個方法來建立新的最新清單。</span><span class="sxs-lookup"><span data-stu-id="3b3ed-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="3b3ed-110">這個方法的後續呼叫將不會影響現有的清單。</span><span class="sxs-lookup"><span data-stu-id="3b3ed-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="3b3ed-111">如果處理序已終止， `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED HRESULT 值將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3b3ed-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b3ed-112">需求</span><span class="sxs-lookup"><span data-stu-id="3b3ed-112">Requirements</span></span>  
 <span data-ttu-id="3b3ed-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b3ed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b3ed-114">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3b3ed-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3b3ed-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b3ed-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b3ed-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b3ed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b3ed-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b3ed-117">See also</span></span>

- [<span data-ttu-id="3b3ed-118">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="3b3ed-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
