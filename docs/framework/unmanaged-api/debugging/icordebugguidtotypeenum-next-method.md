---
title: "ICorDebugGuidToTypeEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bcfbcfb85fc5eb1d58142af4e7d825162e9861b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="25661-102">ICorDebugGuidToTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="25661-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="25661-103">取得指定的數目[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)對應輸入資訊的 Guid 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="25661-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25661-104">語法</span><span class="sxs-lookup"><span data-stu-id="25661-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25661-105">參數</span><span class="sxs-lookup"><span data-stu-id="25661-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="25661-106">[in]要擷取的 GUID 型別對應物件數目。</span><span class="sxs-lookup"><span data-stu-id="25661-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="25661-107">[out]陣列的指標，其中每個指向[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)對應物件[!INCLUDE[wrt](../../../../includes/wrt-md.md)]對應 ICorDebugType 物件的 GUID。</span><span class="sxs-lookup"><span data-stu-id="25661-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="25661-108">[out]數目的指標[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)中實際傳回的物件`values`。</span><span class="sxs-lookup"><span data-stu-id="25661-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25661-109">備註</span><span class="sxs-lookup"><span data-stu-id="25661-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25661-110">需求</span><span class="sxs-lookup"><span data-stu-id="25661-110">Requirements</span></span>  
 <span data-ttu-id="25661-111">**平台：**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25661-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="25661-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25661-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25661-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25661-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25661-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25661-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25661-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="25661-115">See Also</span></span>  
 [<span data-ttu-id="25661-116">ICorDebugGuidToTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="25661-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [<span data-ttu-id="25661-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="25661-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
