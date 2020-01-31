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
ms.openlocfilehash: 39833b689f28437b4241d9cb15fb4a92b2f9bcc3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791380"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="ee58f-102">ICorDebugThread4::GetBlockingObjects 方法</span><span class="sxs-lookup"><span data-stu-id="ee58f-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="ee58f-103">提供[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構的已排序列舉，以提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="ee58f-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee58f-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee58f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee58f-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee58f-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="ee58f-106">脫銷[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構之已排序列舉的指標。</span><span class="sxs-lookup"><span data-stu-id="ee58f-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee58f-107">備註</span><span class="sxs-lookup"><span data-stu-id="ee58f-107">Remarks</span></span>  
 <span data-ttu-id="ee58f-108">傳回之列舉中的第一個專案會對應至封鎖執行緒的第一個結構。</span><span class="sxs-lookup"><span data-stu-id="ee58f-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="ee58f-109">第二個元素對應至在執行非同步程序呼叫（APC）時，在第一個專案上被封鎖時所遇到的封鎖專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="ee58f-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="ee58f-110">列舉只在目前已同步處理狀態的持續時間內有效。</span><span class="sxs-lookup"><span data-stu-id="ee58f-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="ee58f-111">當調試物件處於已同步處理的狀態時，必須呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="ee58f-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="ee58f-112">如果 `ppBlockingObjectEnum` 不是有效的指標，則結果會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="ee58f-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="ee58f-113">如果執行緒遭到封鎖，而且無法判斷錯誤，則方法會傳回表示失敗的 HRESULT;否則，它會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ee58f-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee58f-114">需求</span><span class="sxs-lookup"><span data-stu-id="ee58f-114">Requirements</span></span>  
 <span data-ttu-id="ee58f-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee58f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee58f-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee58f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee58f-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee58f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee58f-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee58f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee58f-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee58f-119">See also</span></span>

- [<span data-ttu-id="ee58f-120">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="ee58f-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="ee58f-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ee58f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ee58f-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="ee58f-122">Debugging</span></span>](index.md)
