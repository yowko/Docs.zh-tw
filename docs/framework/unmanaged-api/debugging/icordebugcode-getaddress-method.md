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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7df668487601e4278b56e196a43d1154b643fd29
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700738"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="24f93-102">ICorDebugCode::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="24f93-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="24f93-103">取得此「ICorDebugCode」介面所代表之程式碼區段的相對虛擬位址（RVA）。</span><span class="sxs-lookup"><span data-stu-id="24f93-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f93-104">語法</span><span class="sxs-lookup"><span data-stu-id="24f93-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24f93-105">參數</span><span class="sxs-lookup"><span data-stu-id="24f93-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="24f93-106">脫銷程式碼區段之 RVA 的指標。</span><span class="sxs-lookup"><span data-stu-id="24f93-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24f93-107">需求</span><span class="sxs-lookup"><span data-stu-id="24f93-107">Requirements</span></span>  
 <span data-ttu-id="24f93-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24f93-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24f93-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24f93-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24f93-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24f93-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24f93-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24f93-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
