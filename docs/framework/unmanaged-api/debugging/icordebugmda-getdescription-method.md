---
title: "ICorDebugMDA::GetDescription 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetDescription
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d527f22693ca912d33d56ae4f0ffeddb9de38ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="6c2aa-102">ICorDebugMDA::GetDescription 方法</span><span class="sxs-lookup"><span data-stu-id="6c2aa-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="6c2aa-103">取得字串，包含由 managed 偵錯助理 (MDA) 的描述[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="6c2aa-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c2aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c2aa-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c2aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c2aa-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6c2aa-106">[in]將會儲存描述字串緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="6c2aa-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6c2aa-107">[out]傳回在字串緩衝區的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="6c2aa-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="6c2aa-108">[out]包含描述 MDA 的字串緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6c2aa-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c2aa-109">備註</span><span class="sxs-lookup"><span data-stu-id="6c2aa-109">Remarks</span></span>  
 <span data-ttu-id="6c2aa-110">字串可以是零長度。</span><span class="sxs-lookup"><span data-stu-id="6c2aa-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c2aa-111">需求</span><span class="sxs-lookup"><span data-stu-id="6c2aa-111">Requirements</span></span>  
 <span data-ttu-id="6c2aa-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c2aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c2aa-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c2aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c2aa-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c2aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c2aa-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c2aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c2aa-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c2aa-116">See Also</span></span>  
 [<span data-ttu-id="6c2aa-117">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="6c2aa-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="6c2aa-118">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="6c2aa-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
