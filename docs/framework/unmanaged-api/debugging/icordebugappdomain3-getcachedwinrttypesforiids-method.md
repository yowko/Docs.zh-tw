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
ms.openlocfilehash: 0369cc6d98736542b764e5914d733a9341753b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088872"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="aef7c-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法</span><span class="sxs-lookup"><span data-stu-id="aef7c-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="aef7c-103">根據介面識別碼，取得應用程式域中快取 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="aef7c-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="aef7c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef7c-105">參數</span><span class="sxs-lookup"><span data-stu-id="aef7c-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="aef7c-106">在必要類型的數目。</span><span class="sxs-lookup"><span data-stu-id="aef7c-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="aef7c-107">在陣列的指標，其中包含對應至要抓取之 Windows 執行階段類型之 managed 表示的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="aef7c-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="aef7c-108">脫銷「ICorDebugTypeEnum」介面物件位址的指標，可根據 `iidsToResolve`中的介面識別碼，列舉所抓取之 Windows 執行階段類型的快取 managed 標記法。</span><span class="sxs-lookup"><span data-stu-id="aef7c-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aef7c-109">備註</span><span class="sxs-lookup"><span data-stu-id="aef7c-109">Remarks</span></span>  
 <span data-ttu-id="aef7c-110">如果方法無法抓取特定介面識別碼的資訊，則 "ICorDebugTypeEnum" 集合中對應的專案將會有因數據抓取問題而發生錯誤的 `ELEMENT_TYPE_END` 類型，或針對未知的介面識別碼 `ELEMENT_TYPE_VOID`。</span><span class="sxs-lookup"><span data-stu-id="aef7c-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef7c-111">需求</span><span class="sxs-lookup"><span data-stu-id="aef7c-111">Requirements</span></span>  
 <span data-ttu-id="aef7c-112">**平臺：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="aef7c-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="aef7c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aef7c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aef7c-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aef7c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aef7c-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef7c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef7c-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="aef7c-116">See also</span></span>

- [<span data-ttu-id="aef7c-117">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="aef7c-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
