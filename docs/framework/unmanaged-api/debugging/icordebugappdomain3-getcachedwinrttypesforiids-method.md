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
ms.openlocfilehash: 601110d37fabbff01aeb14d8ca69a27a2463353f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491403"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="58af7-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法</span><span class="sxs-lookup"><span data-stu-id="58af7-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="58af7-103">取得列舉值的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]其介面識別項為基礎的應用程式定義域中的類型。</span><span class="sxs-lookup"><span data-stu-id="58af7-103">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58af7-104">語法</span><span class="sxs-lookup"><span data-stu-id="58af7-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58af7-105">參數</span><span class="sxs-lookup"><span data-stu-id="58af7-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="58af7-106">[in]必要的型別數目。</span><span class="sxs-lookup"><span data-stu-id="58af7-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="58af7-107">[in]指標陣列，其中包含對應至受管理的表示法的介面識別碼[!INCLUDE[wrt](../../../../includes/wrt-md.md)]要擷取的型別。</span><span class="sxs-lookup"><span data-stu-id="58af7-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="58af7-108">[out]允許的快取列舉"ICorDebugTypeEnum 」 介面物件的位址指標受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]擷取類型，根據中的介面識別項`iidsToResolve`。</span><span class="sxs-lookup"><span data-stu-id="58af7-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58af7-109">備註</span><span class="sxs-lookup"><span data-stu-id="58af7-109">Remarks</span></span>  
 <span data-ttu-id="58af7-110">如果方法無法擷取特定的介面識別項的資訊，「 ICorDebugTypeEnum 」 集合中的對應項目會有一種`ELEMENT_TYPE_END`的資料擷取問題，因為錯誤或`ELEMENT_TYPE_VOID`未知的介面識別項。</span><span class="sxs-lookup"><span data-stu-id="58af7-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58af7-111">需求</span><span class="sxs-lookup"><span data-stu-id="58af7-111">Requirements</span></span>  
 <span data-ttu-id="58af7-112">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58af7-112">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="58af7-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58af7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58af7-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58af7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58af7-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58af7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58af7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58af7-116">See also</span></span>
- [<span data-ttu-id="58af7-117">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="58af7-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
