---
title: ICorDebugValue::GetAddress 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 467ba53f90081f0c3499fb22acab96b5e380a3f4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395835"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="bd221-102">ICorDebugValue::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="bd221-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="bd221-103">取得此 "ICorDebugValue" 物件的位址，此為正在進行調試的進程。</span><span class="sxs-lookup"><span data-stu-id="bd221-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd221-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd221-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd221-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd221-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="bd221-106">脫銷`CORDB_ADDRESS`物件的指標，指定此值物件的位址。</span><span class="sxs-lookup"><span data-stu-id="bd221-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd221-107">備註</span><span class="sxs-lookup"><span data-stu-id="bd221-107">Remarks</span></span>  
 <span data-ttu-id="bd221-108">如果無法使用此值，則會傳回0（零）。</span><span class="sxs-lookup"><span data-stu-id="bd221-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="bd221-109">如果值至少部分在暫存器中，或儲存在垃圾收集行程控制碼（）中，就會發生這種情況 `GCHandle` 。</span><span class="sxs-lookup"><span data-stu-id="bd221-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd221-110">需求</span><span class="sxs-lookup"><span data-stu-id="bd221-110">Requirements</span></span>  
 <span data-ttu-id="bd221-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd221-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd221-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd221-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd221-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd221-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd221-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd221-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd221-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd221-115">See also</span></span>
