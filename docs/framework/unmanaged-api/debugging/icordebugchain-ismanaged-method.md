---
title: ICorDebugChain::IsManaged 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: 55036fcdbd186f91c0e94fb05f3023cf614751f7
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894256"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="bad75-102">ICorDebugChain::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="bad75-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="bad75-103">取得值，指出這個鏈是否正在執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="bad75-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad75-104">語法</span><span class="sxs-lookup"><span data-stu-id="bad75-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bad75-105">參數</span><span class="sxs-lookup"><span data-stu-id="bad75-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="bad75-106">脫銷`true`如果這個鏈正在執行 managed 程式碼，則為，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="bad75-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bad75-107">需求</span><span class="sxs-lookup"><span data-stu-id="bad75-107">Requirements</span></span>  
 <span data-ttu-id="bad75-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bad75-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad75-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bad75-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bad75-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bad75-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bad75-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bad75-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
