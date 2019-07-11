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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f334b4a28b0573fa938c2fda340c0c03175ff18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756885"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="784c7-102">ICorDebugGuidToTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="784c7-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="784c7-103">取得指定的數目[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)對應 Guid 型別資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="784c7-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="784c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="784c7-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="784c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="784c7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="784c7-106">[in]要擷取的 GUID 型別對應物件的數目。</span><span class="sxs-lookup"><span data-stu-id="784c7-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="784c7-107">[out]指標的陣列，其中每一個指向[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)將 Windows 執行階段 GUID 對應至其對應的 ICorDebugType 物件的物件。</span><span class="sxs-lookup"><span data-stu-id="784c7-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="784c7-108">[out]指標的數目[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)物件中實際傳回`values`。</span><span class="sxs-lookup"><span data-stu-id="784c7-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="784c7-109">備註</span><span class="sxs-lookup"><span data-stu-id="784c7-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="784c7-110">需求</span><span class="sxs-lookup"><span data-stu-id="784c7-110">Requirements</span></span>  
 <span data-ttu-id="784c7-111">**平台：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="784c7-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="784c7-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="784c7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="784c7-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="784c7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="784c7-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="784c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="784c7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="784c7-115">See also</span></span>

- [<span data-ttu-id="784c7-116">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="784c7-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="784c7-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="784c7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
