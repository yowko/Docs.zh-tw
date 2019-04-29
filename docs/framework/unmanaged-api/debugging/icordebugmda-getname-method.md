---
title: ICorDebugMDA::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f62fa23d30a93f863cb2be0fa060bd2eba8dca1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723052"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="5e1a3-102">ICorDebugMDA::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="5e1a3-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="5e1a3-103">取得字串，包含由受管理的偵錯助理 (MDA) 的名稱[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="5e1a3-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e1a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e1a3-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e1a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e1a3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5e1a3-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="5e1a3-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5e1a3-107">[out]名稱長度的指標。</span><span class="sxs-lookup"><span data-stu-id="5e1a3-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="5e1a3-108">[out]用來儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="5e1a3-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e1a3-109">備註</span><span class="sxs-lookup"><span data-stu-id="5e1a3-109">Remarks</span></span>  
 <span data-ttu-id="5e1a3-110">MDA 名稱是唯一的值。</span><span class="sxs-lookup"><span data-stu-id="5e1a3-110">MDA names are unique values.</span></span> <span data-ttu-id="5e1a3-111">`GetName`方法是取得 XML 資料流，以及從結構描述為基礎的資料流中擷取名稱方便能替代方式。</span><span class="sxs-lookup"><span data-stu-id="5e1a3-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e1a3-112">需求</span><span class="sxs-lookup"><span data-stu-id="5e1a3-112">Requirements</span></span>  
 <span data-ttu-id="5e1a3-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e1a3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e1a3-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e1a3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e1a3-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e1a3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e1a3-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e1a3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1a3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e1a3-117">See also</span></span>

- [<span data-ttu-id="5e1a3-118">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="5e1a3-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="5e1a3-119">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="5e1a3-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
