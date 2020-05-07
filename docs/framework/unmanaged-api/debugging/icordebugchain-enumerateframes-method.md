---
title: ICorDebugChain::EnumerateFrames 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: c8a62d8b4a4db0f36d991c32dbfc5bad68780f1b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894686"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="59088-102">ICorDebugChain::EnumerateFrames 方法</span><span class="sxs-lookup"><span data-stu-id="59088-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="59088-103">取得列舉值，其中包含鏈中的所有 managed 堆疊框架，從最新的框架開始。</span><span class="sxs-lookup"><span data-stu-id="59088-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59088-104">語法</span><span class="sxs-lookup"><span data-stu-id="59088-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59088-105">參數</span><span class="sxs-lookup"><span data-stu-id="59088-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="59088-106">脫銷ICorDebugFrameEnum 物件位址的指標，這是堆疊框架的列舉值。</span><span class="sxs-lookup"><span data-stu-id="59088-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59088-107">備註</span><span class="sxs-lookup"><span data-stu-id="59088-107">Remarks</span></span>  
 <span data-ttu-id="59088-108">鏈代表執行緒的實體呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="59088-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="59088-109">應該`EnumerateFrames`只針對受管理的鏈呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="59088-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="59088-110">偵錯工具開發介面不會提供方法來取得未受管理的鏈中包含的框架。</span><span class="sxs-lookup"><span data-stu-id="59088-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="59088-111">偵錯工具必須使用其他方法來取得此資訊。</span><span class="sxs-lookup"><span data-stu-id="59088-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59088-112">需求</span><span class="sxs-lookup"><span data-stu-id="59088-112">Requirements</span></span>  
 <span data-ttu-id="59088-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59088-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59088-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59088-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59088-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59088-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59088-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59088-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
