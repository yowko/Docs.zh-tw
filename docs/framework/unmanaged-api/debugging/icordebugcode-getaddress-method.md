---
title: ICorDebugCode::GetAddress 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
ms.openlocfilehash: df73663f714b0c1c3d3ae5dfb53e8e84196a8f37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125687"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="b116e-102">ICorDebugCode::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="b116e-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="b116e-103">取得此「ICorDebugCode」介面所代表之程式碼區段的相對虛擬位址（RVA）。</span><span class="sxs-lookup"><span data-stu-id="b116e-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b116e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b116e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b116e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b116e-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="b116e-106">脫銷程式碼區段之 RVA 的指標。</span><span class="sxs-lookup"><span data-stu-id="b116e-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b116e-107">需求</span><span class="sxs-lookup"><span data-stu-id="b116e-107">Requirements</span></span>  
 <span data-ttu-id="b116e-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b116e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b116e-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b116e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b116e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b116e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b116e-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b116e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
