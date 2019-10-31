---
title: ICorDebugGuidToTypeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: f6f190cd5b2f208df5a4ed88b650af671f2e6c5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138523"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="5a238-102">ICorDebugGuidToTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="5a238-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="5a238-103">取得將 Guid 對應至類型資訊的指定[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)實例數目。</span><span class="sxs-lookup"><span data-stu-id="5a238-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a238-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a238-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a238-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a238-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5a238-106">在要抓取的 GUID 型別對應物件的數目。</span><span class="sxs-lookup"><span data-stu-id="5a238-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="5a238-107">脫銷指標的陣列，其中每一個都會指向[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)物件，它會將 Windows 執行階段 GUID 對應至其相對應的 ICorDebugType 物件。</span><span class="sxs-lookup"><span data-stu-id="5a238-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5a238-108">脫銷`values`中實際傳回之[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="5a238-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a238-109">備註</span><span class="sxs-lookup"><span data-stu-id="5a238-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a238-110">需求</span><span class="sxs-lookup"><span data-stu-id="5a238-110">Requirements</span></span>  
 <span data-ttu-id="5a238-111">**平臺：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="5a238-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="5a238-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a238-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a238-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a238-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a238-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a238-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a238-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a238-115">See also</span></span>

- [<span data-ttu-id="5a238-116">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5a238-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="5a238-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5a238-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
