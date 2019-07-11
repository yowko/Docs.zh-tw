---
title: ICorDebugAppDomainEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12787382686cc056c157ed7a6e8e4984ab93588f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737620"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="15fcc-102">ICorDebugAppDomainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="15fcc-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="15fcc-103">從集合中，從目前游標位置開始，取得指定的應用程式定義域數目。</span><span class="sxs-lookup"><span data-stu-id="15fcc-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15fcc-104">語法</span><span class="sxs-lookup"><span data-stu-id="15fcc-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15fcc-105">參數</span><span class="sxs-lookup"><span data-stu-id="15fcc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="15fcc-106">[in]要擷取的應用程式定義域數目。</span><span class="sxs-lookup"><span data-stu-id="15fcc-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="15fcc-107">[out]指標的陣列，其中每一個指向 ICorDebugAppDomain 物件，表示應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="15fcc-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="15fcc-108">[out]實際傳回的應用程式定義域數目指標。</span><span class="sxs-lookup"><span data-stu-id="15fcc-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="15fcc-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="15fcc-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15fcc-110">需求</span><span class="sxs-lookup"><span data-stu-id="15fcc-110">Requirements</span></span>  
 <span data-ttu-id="15fcc-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15fcc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15fcc-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15fcc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15fcc-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15fcc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15fcc-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15fcc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
