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
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179067"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="6d3eb-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法</span><span class="sxs-lookup"><span data-stu-id="6d3eb-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="6d3eb-103">根據應用程式域中的介面識別碼獲取應用程式域中緩存的 Windows 運行時類型的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="6d3eb-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d3eb-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d3eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d3eb-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d3eb-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="6d3eb-106">[在]所需類型的數量。</span><span class="sxs-lookup"><span data-stu-id="6d3eb-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="6d3eb-107">[在]指向陣列的指標，其中包含與要檢索的 Windows 運行時類型的託管表示形式對應的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="6d3eb-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="6d3eb-108">[出]指向"ICorDebugTypeEnum"介面物件的位址的指標，該物件允許根據 中的`iidsToResolve`介面識別碼檢索到已檢索的 Windows 運行時類型的緩存託管表示形式。</span><span class="sxs-lookup"><span data-stu-id="6d3eb-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d3eb-109">備註</span><span class="sxs-lookup"><span data-stu-id="6d3eb-109">Remarks</span></span>  
 <span data-ttu-id="6d3eb-110">如果方法無法檢索特定介面識別碼的資訊，則"ICorDebugTypeEnum"集合中的相應條目將具有一種`ELEMENT_TYPE_END`因數據檢索問題或`ELEMENT_TYPE_VOID`未知介面識別碼而導致的錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="6d3eb-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d3eb-111">需求</span><span class="sxs-lookup"><span data-stu-id="6d3eb-111">Requirements</span></span>  
 <span data-ttu-id="6d3eb-112">**平臺：** 視窗運行時</span><span class="sxs-lookup"><span data-stu-id="6d3eb-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="6d3eb-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d3eb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d3eb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d3eb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d3eb-115">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d3eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3eb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d3eb-116">See also</span></span>

- [<span data-ttu-id="6d3eb-117">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="6d3eb-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
