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
ms.openlocfilehash: 64e697323377d664b7b1e36bbf5931a44465cc51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178962"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="586a2-102">ICorDebugChain::GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="586a2-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="586a2-103">獲取此鏈的堆疊段的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="586a2-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="586a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="586a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="586a2-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="586a2-106">[出]指向作為堆疊`CORDB_ADDRESS`段起始位址的值的指標。</span><span class="sxs-lookup"><span data-stu-id="586a2-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="586a2-107">[出]指向作為堆疊`CORDB_ADDRESS`段結束位址的值的指標。</span><span class="sxs-lookup"><span data-stu-id="586a2-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="586a2-108">備註</span><span class="sxs-lookup"><span data-stu-id="586a2-108">Remarks</span></span>  
 <span data-ttu-id="586a2-109">數值範圍僅對堆疊幀位置的比較有意義。</span><span class="sxs-lookup"><span data-stu-id="586a2-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="586a2-110">您不能對堆疊中實際存儲的內容進行任何假設。</span><span class="sxs-lookup"><span data-stu-id="586a2-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="586a2-111">需求</span><span class="sxs-lookup"><span data-stu-id="586a2-111">Requirements</span></span>  
 <span data-ttu-id="586a2-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="586a2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="586a2-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="586a2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="586a2-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="586a2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="586a2-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="586a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
