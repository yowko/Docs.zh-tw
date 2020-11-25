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
ms.openlocfilehash: 2acf8fb507ab617e066a31c9c2657b1ef0d18e47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693277"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="91d2c-102">ICorPublishProcess::EnumAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="91d2c-102">ICorPublishProcess::EnumAppDomains Method</span></span>

<span data-ttu-id="91d2c-103">取得此 [ICorPublishProcess](icorpublishprocess-interface.md)所參考之進程中的應用程式域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="91d2c-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d2c-104">語法</span><span class="sxs-lookup"><span data-stu-id="91d2c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91d2c-105">參數</span><span class="sxs-lookup"><span data-stu-id="91d2c-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="91d2c-106">擴展 [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) 實例位址的指標，可讓您在這個進程中，透過應用程式域的集合進行反復專案。</span><span class="sxs-lookup"><span data-stu-id="91d2c-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91d2c-107">備註</span><span class="sxs-lookup"><span data-stu-id="91d2c-107">Remarks</span></span>  

 <span data-ttu-id="91d2c-108">應用程式域的清單是以呼叫方法時存在的應用程式域的快照集為基礎 `EnumAppDomains` 。</span><span class="sxs-lookup"><span data-stu-id="91d2c-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="91d2c-109">您可以多次呼叫這個方法來建立新的最新清單。</span><span class="sxs-lookup"><span data-stu-id="91d2c-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="91d2c-110">後續呼叫這個方法不會影響現有的清單。</span><span class="sxs-lookup"><span data-stu-id="91d2c-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="91d2c-111">如果進程已結束， `EnumAppDomains` 將會失敗，並出現 CORDBG_E_PROCESS_TERMINATED 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="91d2c-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d2c-112">需求</span><span class="sxs-lookup"><span data-stu-id="91d2c-112">Requirements</span></span>  

 <span data-ttu-id="91d2c-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91d2c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91d2c-114">**標頭：** CorPub .idl、CorPub。h</span><span class="sxs-lookup"><span data-stu-id="91d2c-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="91d2c-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91d2c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91d2c-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91d2c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d2c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d2c-117">See also</span></span>

- [<span data-ttu-id="91d2c-118">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="91d2c-118">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
