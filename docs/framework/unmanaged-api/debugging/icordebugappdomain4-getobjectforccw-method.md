---
title: ICorDebugAppDomain4::GetObjectForCCW 方法
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1089668aa19747f5f694360ebb87098e2df9ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405547"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="87ea3-102">ICorDebugAppDomain4::GetObjectForCCW 方法</span><span class="sxs-lookup"><span data-stu-id="87ea3-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="87ea3-103">從 COM 可呼叫包裝函式 (CCW) 指標取得 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="87ea3-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ea3-104">語法</span><span class="sxs-lookup"><span data-stu-id="87ea3-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87ea3-105">參數</span><span class="sxs-lookup"><span data-stu-id="87ea3-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="87ea3-106">[in] COM 可呼叫包裝函式 (CCW) 指標。</span><span class="sxs-lookup"><span data-stu-id="87ea3-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="87ea3-107">[out]"ICorDebugValue 」 物件，代表指定 CCW 指標對應之 managed 的物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="87ea3-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ea3-108">備註</span><span class="sxs-lookup"><span data-stu-id="87ea3-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ea3-109">需求</span><span class="sxs-lookup"><span data-stu-id="87ea3-109">Requirements</span></span>  
 <span data-ttu-id="87ea3-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87ea3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ea3-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87ea3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87ea3-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87ea3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87ea3-113">**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ea3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ea3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87ea3-114">See Also</span></span>  
 [<span data-ttu-id="87ea3-115">ICorDebugAppDomain4 介面</span><span class="sxs-lookup"><span data-stu-id="87ea3-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="87ea3-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="87ea3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
