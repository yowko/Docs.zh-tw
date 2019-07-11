---
title: ICorDebugEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f823f660efee2d53bc1f6fa50d8878f496417379
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752284"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="da416-102">ICorDebugEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="da416-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="da416-103">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="da416-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da416-104">語法</span><span class="sxs-lookup"><span data-stu-id="da416-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da416-105">參數</span><span class="sxs-lookup"><span data-stu-id="da416-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="da416-106">[out]列舉中的項目數目指標。</span><span class="sxs-lookup"><span data-stu-id="da416-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da416-107">需求</span><span class="sxs-lookup"><span data-stu-id="da416-107">Requirements</span></span>  
 <span data-ttu-id="da416-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da416-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da416-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da416-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da416-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da416-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da416-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da416-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
