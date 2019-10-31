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
ms.openlocfilehash: 208d5d2e3ca571a1c23a9322c05e784bd2238d61
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124690"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="2f7dd-102">ICorDebugEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="2f7dd-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="2f7dd-103">取得列舉中的專案數。</span><span class="sxs-lookup"><span data-stu-id="2f7dd-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f7dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f7dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f7dd-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f7dd-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="2f7dd-106">脫銷列舉中專案數的指標。</span><span class="sxs-lookup"><span data-stu-id="2f7dd-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f7dd-107">需求</span><span class="sxs-lookup"><span data-stu-id="2f7dd-107">Requirements</span></span>  
 <span data-ttu-id="2f7dd-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f7dd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f7dd-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f7dd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f7dd-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f7dd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f7dd-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f7dd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
