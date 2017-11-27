---
title: "ICorDebugProcess5::GetObject 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8966b113e331488a27664de8d42eca4c2db5e51e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="55260-102">ICorDebugProcess5::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="55260-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="55260-103">將物件位址轉換為"ICorDebugObjectValue 」 物件。</span><span class="sxs-lookup"><span data-stu-id="55260-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55260-104">語法</span><span class="sxs-lookup"><span data-stu-id="55260-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55260-105">參數</span><span class="sxs-lookup"><span data-stu-id="55260-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="55260-106">[in]物件的位址。</span><span class="sxs-lookup"><span data-stu-id="55260-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="55260-107">[out]「 ICorDebugObjectValue 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="55260-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55260-108">備註</span><span class="sxs-lookup"><span data-stu-id="55260-108">Remarks</span></span>  
 <span data-ttu-id="55260-109">如果`addr`並未指向有效的 managed 物件`GetObject`方法會傳回`E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="55260-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55260-110">需求</span><span class="sxs-lookup"><span data-stu-id="55260-110">Requirements</span></span>  
 <span data-ttu-id="55260-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55260-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55260-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55260-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55260-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55260-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55260-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55260-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55260-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55260-115">See Also</span></span>  
 [<span data-ttu-id="55260-116">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="55260-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="55260-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="55260-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
