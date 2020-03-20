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
ms.openlocfilehash: 4b48132ee60bcaebb218d8f583de6558372f5055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178602"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="6e107-102">ICorDebugProcess5::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="6e107-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="6e107-103">將物件位址轉換為"ICorDebugObjectValue"物件。</span><span class="sxs-lookup"><span data-stu-id="6e107-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e107-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e107-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e107-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e107-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="6e107-106">[在]物件位址。</span><span class="sxs-lookup"><span data-stu-id="6e107-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="6e107-107">[出]指向"ICorDebugObjectValue"物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="6e107-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e107-108">備註</span><span class="sxs-lookup"><span data-stu-id="6e107-108">Remarks</span></span>  
 <span data-ttu-id="6e107-109">如果不`addr`指向有效的託管物件，`GetObject`則 方法將返回`E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="6e107-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e107-110">需求</span><span class="sxs-lookup"><span data-stu-id="6e107-110">Requirements</span></span>  
 <span data-ttu-id="6e107-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e107-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e107-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e107-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e107-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e107-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e107-114">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e107-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e107-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e107-115">See also</span></span>

- [<span data-ttu-id="6e107-116">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="6e107-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="6e107-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6e107-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
