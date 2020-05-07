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
ms.openlocfilehash: f9b00d5e34300f1ed16eaddff3bf8e877219f910
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893792"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="edec9-102">ICorDebugCode::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="edec9-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="edec9-103">取得此「ICorDebugCode」介面所代表之程式碼區段的相對虛擬位址（RVA）。</span><span class="sxs-lookup"><span data-stu-id="edec9-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edec9-104">語法</span><span class="sxs-lookup"><span data-stu-id="edec9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edec9-105">參數</span><span class="sxs-lookup"><span data-stu-id="edec9-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="edec9-106">脫銷程式碼區段之 RVA 的指標。</span><span class="sxs-lookup"><span data-stu-id="edec9-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edec9-107">需求</span><span class="sxs-lookup"><span data-stu-id="edec9-107">Requirements</span></span>  
 <span data-ttu-id="edec9-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edec9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edec9-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edec9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edec9-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edec9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edec9-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edec9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
