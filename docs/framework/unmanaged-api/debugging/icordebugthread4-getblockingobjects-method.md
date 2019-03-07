---
title: ICorDebugThread4::GetBlockingObjects 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca6b057225ce4d453cd156bea9f941369586cd81
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473757"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="eb2df-102">ICorDebugThread4::GetBlockingObjects 方法</span><span class="sxs-lookup"><span data-stu-id="eb2df-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="eb2df-103">提供的已排序的列舉[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2df-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2df-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb2df-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb2df-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb2df-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="eb2df-106">[out]已排序列舉型別指標[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="eb2df-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb2df-107">備註</span><span class="sxs-lookup"><span data-stu-id="eb2df-107">Remarks</span></span>  
 <span data-ttu-id="eb2df-108">傳回的列舉型別中的第一個元素會對應至正在封鎖執行緒的第一個結構。</span><span class="sxs-lookup"><span data-stu-id="eb2df-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="eb2df-109">第二個元素對應至 封鎖第一個子集，等等時執行的非同步程序呼叫 (APC) 時所發生的封鎖項目。</span><span class="sxs-lookup"><span data-stu-id="eb2df-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="eb2df-110">列舉型別是有效的只會針對目前的同步處理狀態的持續時間。</span><span class="sxs-lookup"><span data-stu-id="eb2df-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="eb2df-111">偵錯項目處於已同步處理狀態時，必須呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="eb2df-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="eb2df-112">如果`ppBlockingObjectEnum`不是有效的指標，結果為未定義。</span><span class="sxs-lookup"><span data-stu-id="eb2df-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="eb2df-113">如果執行緒遭到封鎖，無法判斷此錯誤，則方法會傳回 HRESULT，表示失敗;否則，它會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="eb2df-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2df-114">需求</span><span class="sxs-lookup"><span data-stu-id="eb2df-114">Requirements</span></span>  
 <span data-ttu-id="eb2df-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb2df-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2df-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb2df-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb2df-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb2df-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb2df-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2df-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2df-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb2df-119">See also</span></span>
- [<span data-ttu-id="eb2df-120">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="eb2df-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="eb2df-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="eb2df-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="eb2df-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="eb2df-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
