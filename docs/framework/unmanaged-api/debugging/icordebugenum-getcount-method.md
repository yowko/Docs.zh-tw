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
ms.openlocfilehash: b4af328c537fbc3b64eb1a2ac3df3a4e4224789e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996017"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="8de88-102">ICorDebugEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="8de88-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="8de88-103">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="8de88-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de88-104">語法</span><span class="sxs-lookup"><span data-stu-id="8de88-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8de88-105">參數</span><span class="sxs-lookup"><span data-stu-id="8de88-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="8de88-106">[out]列舉中的項目數目指標。</span><span class="sxs-lookup"><span data-stu-id="8de88-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de88-107">需求</span><span class="sxs-lookup"><span data-stu-id="8de88-107">Requirements</span></span>  
 <span data-ttu-id="8de88-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8de88-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de88-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8de88-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8de88-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8de88-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8de88-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de88-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
