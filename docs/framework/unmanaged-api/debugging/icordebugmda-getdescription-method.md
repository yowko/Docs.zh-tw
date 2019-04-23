---
title: ICorDebugMDA::GetDescription 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 998d4baf03123f1ffc174b2a7aeed0ff4a25b001
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133470"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="7a3ce-102">ICorDebugMDA::GetDescription 方法</span><span class="sxs-lookup"><span data-stu-id="7a3ce-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="7a3ce-103">取得字串，包含由 managed 偵錯助理 (MDA) 的描述[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="7a3ce-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a3ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a3ce-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a3ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a3ce-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="7a3ce-106">[in]會儲存描述字串緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="7a3ce-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7a3ce-107">[out]傳回字串緩衝區的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="7a3ce-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="7a3ce-108">[out]字串緩衝區，包含描述的 MDA。</span><span class="sxs-lookup"><span data-stu-id="7a3ce-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a3ce-109">備註</span><span class="sxs-lookup"><span data-stu-id="7a3ce-109">Remarks</span></span>  
 <span data-ttu-id="7a3ce-110">字串可以是零長度。</span><span class="sxs-lookup"><span data-stu-id="7a3ce-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a3ce-111">需求</span><span class="sxs-lookup"><span data-stu-id="7a3ce-111">Requirements</span></span>  
 <span data-ttu-id="7a3ce-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a3ce-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a3ce-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a3ce-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a3ce-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a3ce-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a3ce-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a3ce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3ce-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a3ce-116">See also</span></span>

- [<span data-ttu-id="7a3ce-117">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="7a3ce-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="7a3ce-118">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="7a3ce-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
