---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95c84f7f40db0096b26ec448f8f229cdbfe3afb1
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025901"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="1f50e-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法</span><span class="sxs-lookup"><span data-stu-id="1f50e-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="1f50e-103">取得其介面識別項為基礎的應用程式定義域中快取的 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1f50e-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f50e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f50e-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f50e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f50e-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="1f50e-106">[in]必要的型別數目。</span><span class="sxs-lookup"><span data-stu-id="1f50e-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="1f50e-107">[in]包含對應至受管理的表示法，要擷取 Windows 執行階段類型的介面識別碼的陣列指標。</span><span class="sxs-lookup"><span data-stu-id="1f50e-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="1f50e-108">[out]擷取可讓受管理的快取表示，Windows 執行階段類型的列舉型別"ICorDebugTypeEnum 」 介面物件的位址指標，根據中的介面識別項`iidsToResolve`。</span><span class="sxs-lookup"><span data-stu-id="1f50e-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f50e-109">備註</span><span class="sxs-lookup"><span data-stu-id="1f50e-109">Remarks</span></span>  
 <span data-ttu-id="1f50e-110">如果方法無法擷取特定的介面識別項的資訊，「 ICorDebugTypeEnum 」 集合中的對應項目會有一種`ELEMENT_TYPE_END`的資料擷取問題，因為錯誤或`ELEMENT_TYPE_VOID`未知的介面識別項。</span><span class="sxs-lookup"><span data-stu-id="1f50e-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f50e-111">需求</span><span class="sxs-lookup"><span data-stu-id="1f50e-111">Requirements</span></span>  
 <span data-ttu-id="1f50e-112">**平台：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="1f50e-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="1f50e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f50e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f50e-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f50e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f50e-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f50e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f50e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f50e-116">See also</span></span>

- [<span data-ttu-id="1f50e-117">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="1f50e-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
