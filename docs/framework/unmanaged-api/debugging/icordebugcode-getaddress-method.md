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
ms.openlocfilehash: e2de22729fd3d7a511c1105ebf810d0402bd73a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402079"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="1ecae-102">ICorDebugCode::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="1ecae-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="1ecae-103">取得此"ICorDebugCode 」 介面代表的程式碼片段的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="1ecae-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ecae-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ecae-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ecae-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ecae-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="1ecae-106">[out]程式碼區段的 RVA 指標。</span><span class="sxs-lookup"><span data-stu-id="1ecae-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ecae-107">需求</span><span class="sxs-lookup"><span data-stu-id="1ecae-107">Requirements</span></span>  
 <span data-ttu-id="1ecae-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ecae-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ecae-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ecae-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ecae-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ecae-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ecae-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ecae-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ecae-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ecae-112">See Also</span></span>  
 
