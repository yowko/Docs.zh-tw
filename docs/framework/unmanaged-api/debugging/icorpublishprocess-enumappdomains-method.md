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
ms.openlocfilehash: 4799c1d04e8172c604eeec50f2b841a6db063949
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790575"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="a8168-102">ICorPublishProcess::EnumAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="a8168-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="a8168-103">取得此[ICorPublishProcess](icorpublishprocess-interface.md)所參考之進程中應用程式域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a8168-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8168-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8168-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8168-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8168-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a8168-106">脫銷[ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)實例位址的指標，允許在此進程中逐一查看應用程式域的集合。</span><span class="sxs-lookup"><span data-stu-id="a8168-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8168-107">備註</span><span class="sxs-lookup"><span data-stu-id="a8168-107">Remarks</span></span>  
 <span data-ttu-id="a8168-108">應用程式域的清單是以呼叫 `EnumAppDomains` 方法時存在的應用程式域快照集為基礎。</span><span class="sxs-lookup"><span data-stu-id="a8168-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="a8168-109">這個方法可以被呼叫一次以上，以建立新的最新清單。</span><span class="sxs-lookup"><span data-stu-id="a8168-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="a8168-110">此方法的後續呼叫將不會影響現有的清單。</span><span class="sxs-lookup"><span data-stu-id="a8168-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="a8168-111">如果進程已經終止，`EnumAppDomains` 將會失敗，並出現 CORDBG_E_PROCESS_TERMINATED 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="a8168-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8168-112">需求</span><span class="sxs-lookup"><span data-stu-id="a8168-112">Requirements</span></span>  
 <span data-ttu-id="a8168-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8168-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8168-114">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="a8168-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a8168-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8168-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8168-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8168-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8168-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a8168-117">See also</span></span>

- [<span data-ttu-id="a8168-118">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="a8168-118">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
