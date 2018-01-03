---
title: "ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a7ce44dcfc709b4fea1952471cf31f5f07d4d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="7eea3-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法</span><span class="sxs-lookup"><span data-stu-id="7eea3-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="7eea3-103">取得列舉值的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]應用程式定義域中的類型取決於其介面識別項。</span><span class="sxs-lookup"><span data-stu-id="7eea3-103">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eea3-104">語法</span><span class="sxs-lookup"><span data-stu-id="7eea3-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7eea3-105">參數</span><span class="sxs-lookup"><span data-stu-id="7eea3-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="7eea3-106">[in]必要的型別數目。</span><span class="sxs-lookup"><span data-stu-id="7eea3-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="7eea3-107">[in]指標陣列，其中包含對應到受管理的表示法的介面識別碼[!INCLUDE[wrt](../../../../includes/wrt-md.md)]要擷取的類型。</span><span class="sxs-lookup"><span data-stu-id="7eea3-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="7eea3-108">[out]允許的快取列舉"ICorDebugTypeEnum 」 介面物件的位址指標受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]擷取類型，根據中的介面識別碼`iidsToResolve`。</span><span class="sxs-lookup"><span data-stu-id="7eea3-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eea3-109">備註</span><span class="sxs-lookup"><span data-stu-id="7eea3-109">Remarks</span></span>  
 <span data-ttu-id="7eea3-110">如果方法時，無法擷取特定的介面識別項的資訊，"ICorDebugTypeEnum"集合中的對應項目會有一種`ELEMENT_TYPE_END`資料擷取問題，因為錯誤或`ELEMENT_TYPE_VOID`未知的介面識別項。</span><span class="sxs-lookup"><span data-stu-id="7eea3-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eea3-111">需求</span><span class="sxs-lookup"><span data-stu-id="7eea3-111">Requirements</span></span>  
 <span data-ttu-id="7eea3-112">**平台：**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eea3-112">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="7eea3-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7eea3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7eea3-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eea3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eea3-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eea3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eea3-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="7eea3-116">See Also</span></span>  
 [<span data-ttu-id="7eea3-117">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="7eea3-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
