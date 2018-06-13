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
ms.openlocfilehash: 8c9f76f2c3b2ecf3ac5805dea8f8243f0b74ad48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417829"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="e1b58-102">ICorDebugMDA::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="e1b58-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="e1b58-103">取得字串，包含由受管理的偵錯助理 (MDA) 的名稱[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="e1b58-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1b58-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1b58-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1b58-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1b58-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e1b58-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="e1b58-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e1b58-107">[out]名稱長度的指標。</span><span class="sxs-lookup"><span data-stu-id="e1b58-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e1b58-108">[out]用來儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1b58-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1b58-109">備註</span><span class="sxs-lookup"><span data-stu-id="e1b58-109">Remarks</span></span>  
 <span data-ttu-id="e1b58-110">MDA 名稱是唯一的值。</span><span class="sxs-lookup"><span data-stu-id="e1b58-110">MDA names are unique values.</span></span> <span data-ttu-id="e1b58-111">`GetName`方法是方便效能的替代方法來取得 XML 資料流及擷取結構描述為基礎的資料流的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1b58-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1b58-112">需求</span><span class="sxs-lookup"><span data-stu-id="e1b58-112">Requirements</span></span>  
 <span data-ttu-id="e1b58-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1b58-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1b58-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1b58-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1b58-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1b58-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1b58-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1b58-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b58-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1b58-117">See Also</span></span>  
 [<span data-ttu-id="e1b58-118">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="e1b58-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="e1b58-119">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="e1b58-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
