---
title: "ICorDebugProcess5::GetTypeID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f76285fceaa32f7c8b62b5cdf2ae7b4e9ec00de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="63737-102">ICorDebugProcess5::GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="63737-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="63737-103">將轉換的物件位址[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)識別項。</span><span class="sxs-lookup"><span data-stu-id="63737-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63737-104">語法</span><span class="sxs-lookup"><span data-stu-id="63737-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63737-105">參數</span><span class="sxs-lookup"><span data-stu-id="63737-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="63737-106">[in]物件的位址。</span><span class="sxs-lookup"><span data-stu-id="63737-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="63737-107">指標[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)識別物件的值。</span><span class="sxs-lookup"><span data-stu-id="63737-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63737-108">備註</span><span class="sxs-lookup"><span data-stu-id="63737-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63737-109">需求</span><span class="sxs-lookup"><span data-stu-id="63737-109">Requirements</span></span>  
 <span data-ttu-id="63737-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63737-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63737-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63737-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63737-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63737-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63737-113">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63737-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63737-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="63737-114">See Also</span></span>  
 [<span data-ttu-id="63737-115">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="63737-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="63737-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="63737-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
