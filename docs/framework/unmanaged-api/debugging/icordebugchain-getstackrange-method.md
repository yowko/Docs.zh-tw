---
title: ICorDebugChain::GetStackRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: d9430c5a1f37a0507b383ea5437f7d7fed706c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123856"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="acd7d-102">ICorDebugChain::GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="acd7d-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="acd7d-103">取得此鏈之堆疊區段的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="acd7d-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd7d-104">語法</span><span class="sxs-lookup"><span data-stu-id="acd7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acd7d-105">參數</span><span class="sxs-lookup"><span data-stu-id="acd7d-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="acd7d-106">脫銷`CORDB_ADDRESS` 值的指標，這是堆疊區段的起始位址。</span><span class="sxs-lookup"><span data-stu-id="acd7d-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="acd7d-107">脫銷指向堆疊區段結尾位址 `CORDB_ADDRESS` 值的指標。</span><span class="sxs-lookup"><span data-stu-id="acd7d-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acd7d-108">備註</span><span class="sxs-lookup"><span data-stu-id="acd7d-108">Remarks</span></span>  
 <span data-ttu-id="acd7d-109">只有在比較堆疊框架位置時，數值範圍才有意義。</span><span class="sxs-lookup"><span data-stu-id="acd7d-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="acd7d-110">您無法針對實際儲存在堆疊上的內容進行任何假設。</span><span class="sxs-lookup"><span data-stu-id="acd7d-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acd7d-111">需求</span><span class="sxs-lookup"><span data-stu-id="acd7d-111">Requirements</span></span>  
 <span data-ttu-id="acd7d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="acd7d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acd7d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acd7d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acd7d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acd7d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acd7d-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acd7d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
