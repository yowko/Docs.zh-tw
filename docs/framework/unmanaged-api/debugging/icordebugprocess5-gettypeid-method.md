---
title: ICorDebugProcess5::GetTypeID 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 6c159780b9019127d166e8437ea4ed214284011f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121256"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="09ccf-102">ICorDebugProcess5::GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="09ccf-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="09ccf-103">將物件位址轉換成[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)識別碼。</span><span class="sxs-lookup"><span data-stu-id="09ccf-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ccf-104">語法</span><span class="sxs-lookup"><span data-stu-id="09ccf-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09ccf-105">參數</span><span class="sxs-lookup"><span data-stu-id="09ccf-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="09ccf-106">在物件位址。</span><span class="sxs-lookup"><span data-stu-id="09ccf-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="09ccf-107">識別物件之[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)值的指標。</span><span class="sxs-lookup"><span data-stu-id="09ccf-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09ccf-108">備註</span><span class="sxs-lookup"><span data-stu-id="09ccf-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ccf-109">需求</span><span class="sxs-lookup"><span data-stu-id="09ccf-109">Requirements</span></span>  
 <span data-ttu-id="09ccf-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09ccf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ccf-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09ccf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09ccf-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09ccf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09ccf-113">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ccf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ccf-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="09ccf-114">See also</span></span>

- [<span data-ttu-id="09ccf-115">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="09ccf-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="09ccf-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="09ccf-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
