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
ms.openlocfilehash: 55251a3adfa67c1dac3b6952a37217e3eeb4c04a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421901"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="f7c7a-102">ICorDebugThread4::GetBlockingObjects 方法</span><span class="sxs-lookup"><span data-stu-id="f7c7a-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="f7c7a-103">提供的已排序的列舉[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c7a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7c7a-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7c7a-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7c7a-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="f7c7a-106">[out]指標的已排序列舉[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7c7a-107">備註</span><span class="sxs-lookup"><span data-stu-id="f7c7a-107">Remarks</span></span>  
 <span data-ttu-id="f7c7a-108">傳回的列舉中的第一個項目會對應至第一個封鎖執行緒的結構。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="f7c7a-109">第二個元素會對應到發生封鎖的第一，等等時執行的非同步程序呼叫 (APC) 時封鎖項目。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="f7c7a-110">列舉型別無效，只會針對目前已同步處理狀態的持續時間。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="f7c7a-111">偵錯項目處於已同步處理狀態時，必須呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="f7c7a-112">如果`ppBlockingObjectEnum`不是有效的指標，結果會是未定義。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="f7c7a-113">如果執行緒被封鎖，而且無法判斷此錯誤，方法會傳回 HRESULT，表示失敗。否則，它會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c7a-114">需求</span><span class="sxs-lookup"><span data-stu-id="f7c7a-114">Requirements</span></span>  
 <span data-ttu-id="f7c7a-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c7a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c7a-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7c7a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7c7a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7c7a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7c7a-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c7a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c7a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7c7a-119">See Also</span></span>  
 [<span data-ttu-id="f7c7a-120">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="f7c7a-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="f7c7a-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f7c7a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f7c7a-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="f7c7a-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
