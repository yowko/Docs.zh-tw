---
title: ICorDebugProcess5::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9588a22feb27d2bd40af2b003179638ef6f34e83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660862"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="f4f09-102">ICorDebugProcess5::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="f4f09-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="f4f09-103">將轉換的物件位址為"ICorDebugObjectValue 」 物件。</span><span class="sxs-lookup"><span data-stu-id="f4f09-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4f09-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4f09-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4f09-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4f09-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="f4f09-106">[in]物件的位址。</span><span class="sxs-lookup"><span data-stu-id="f4f09-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="f4f09-107">[out]「 ICorDebugObjectValue"物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="f4f09-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4f09-108">備註</span><span class="sxs-lookup"><span data-stu-id="f4f09-108">Remarks</span></span>  
 <span data-ttu-id="f4f09-109">如果`addr`並未指向有效的 managed 物件`GetObject`方法會傳回`E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="f4f09-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4f09-110">需求</span><span class="sxs-lookup"><span data-stu-id="f4f09-110">Requirements</span></span>  
 <span data-ttu-id="f4f09-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f09-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4f09-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4f09-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4f09-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4f09-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4f09-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4f09-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4f09-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4f09-115">See also</span></span>
- [<span data-ttu-id="f4f09-116">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="f4f09-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="f4f09-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f4f09-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
