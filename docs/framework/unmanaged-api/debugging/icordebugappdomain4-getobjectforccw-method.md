---
title: ICorDebugAppDomain4::GetObjectForCCW 方法
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: f3e64def16fb2817244ef7669ff4bb7fef0bd07c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684444"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="04ece-102">ICorDebugAppDomain4::GetObjectForCCW 方法</span><span class="sxs-lookup"><span data-stu-id="04ece-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>

<span data-ttu-id="04ece-103">從 COM 可呼叫包裝函式 (CCW) 指標取得 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="04ece-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ece-104">語法</span><span class="sxs-lookup"><span data-stu-id="04ece-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04ece-105">參數</span><span class="sxs-lookup"><span data-stu-id="04ece-105">Parameters</span></span>  

 `ccwPointer`  
 <span data-ttu-id="04ece-106">[in] COM 可呼叫包裝函式 (CCW) 指標。</span><span class="sxs-lookup"><span data-stu-id="04ece-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="04ece-107">擴展"ICorDebugValue" 物件位址的指標，代表對應至指定 CCW 指標的 managed 物件。</span><span class="sxs-lookup"><span data-stu-id="04ece-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04ece-108">備註</span><span class="sxs-lookup"><span data-stu-id="04ece-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ece-109">需求</span><span class="sxs-lookup"><span data-stu-id="04ece-109">Requirements</span></span>  

 <span data-ttu-id="04ece-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04ece-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ece-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04ece-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04ece-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04ece-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04ece-113">**.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04ece-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ece-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04ece-114">See also</span></span>

- [<span data-ttu-id="04ece-115">ICorDebugAppDomain4 介面</span><span class="sxs-lookup"><span data-stu-id="04ece-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="04ece-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="04ece-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
