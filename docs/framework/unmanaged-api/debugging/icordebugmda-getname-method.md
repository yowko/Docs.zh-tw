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
ms.openlocfilehash: 1f0ed1aa0d095b13a90ed5b036719e71ccc8e272
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468191"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="98056-102">ICorDebugMDA::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="98056-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="98056-103">取得字串，包含由受管理的偵錯助理 (MDA) 的名稱[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="98056-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98056-104">語法</span><span class="sxs-lookup"><span data-stu-id="98056-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98056-105">參數</span><span class="sxs-lookup"><span data-stu-id="98056-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="98056-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="98056-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="98056-107">[out]名稱長度的指標。</span><span class="sxs-lookup"><span data-stu-id="98056-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="98056-108">[out]用來儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="98056-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98056-109">備註</span><span class="sxs-lookup"><span data-stu-id="98056-109">Remarks</span></span>  
 <span data-ttu-id="98056-110">MDA 名稱是唯一的值。</span><span class="sxs-lookup"><span data-stu-id="98056-110">MDA names are unique values.</span></span> <span data-ttu-id="98056-111">`GetName`方法是取得 XML 資料流，以及從結構描述為基礎的資料流中擷取名稱方便能替代方式。</span><span class="sxs-lookup"><span data-stu-id="98056-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98056-112">需求</span><span class="sxs-lookup"><span data-stu-id="98056-112">Requirements</span></span>  
 <span data-ttu-id="98056-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98056-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98056-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98056-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98056-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98056-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98056-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98056-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98056-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98056-117">See also</span></span>
- [<span data-ttu-id="98056-118">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="98056-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="98056-119">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="98056-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
