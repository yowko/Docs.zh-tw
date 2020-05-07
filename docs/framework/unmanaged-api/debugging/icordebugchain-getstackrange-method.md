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
ms.openlocfilehash: 40ecc183c32500ad9e88ceb1bfc0528d717430e8
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894459"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="54ece-102">ICorDebugChain::GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="54ece-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="54ece-103">取得此鏈之堆疊區段的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="54ece-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54ece-104">語法</span><span class="sxs-lookup"><span data-stu-id="54ece-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54ece-105">參數</span><span class="sxs-lookup"><span data-stu-id="54ece-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="54ece-106">脫銷`CORDB_ADDRESS`值的指標，這是堆疊區段的起始位址。</span><span class="sxs-lookup"><span data-stu-id="54ece-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="54ece-107">脫銷`CORDB_ADDRESS`值的指標，這是堆疊區段的結束位址。</span><span class="sxs-lookup"><span data-stu-id="54ece-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54ece-108">備註</span><span class="sxs-lookup"><span data-stu-id="54ece-108">Remarks</span></span>  
 <span data-ttu-id="54ece-109">只有在比較堆疊框架位置時，數值範圍才有意義。</span><span class="sxs-lookup"><span data-stu-id="54ece-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="54ece-110">您無法針對實際儲存在堆疊上的內容進行任何假設。</span><span class="sxs-lookup"><span data-stu-id="54ece-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54ece-111">需求</span><span class="sxs-lookup"><span data-stu-id="54ece-111">Requirements</span></span>  
 <span data-ttu-id="54ece-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54ece-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54ece-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54ece-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54ece-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54ece-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54ece-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54ece-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
