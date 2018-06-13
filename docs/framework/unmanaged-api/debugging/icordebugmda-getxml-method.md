---
title: ICorDebugMDA::GetXML 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 874462e37aa10af589f39ed099de899ff7155d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414641"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="3672e-102">ICorDebugMDA::GetXML 方法</span><span class="sxs-lookup"><span data-stu-id="3672e-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="3672e-103">取得由 managed 偵錯助理 (MDA) 相關聯的完整 XML 資料流[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="3672e-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3672e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3672e-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3672e-105">參數</span><span class="sxs-lookup"><span data-stu-id="3672e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3672e-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="3672e-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3672e-107">[out]XML 資料流的長度指標。</span><span class="sxs-lookup"><span data-stu-id="3672e-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="3672e-108">[out]用來儲存 XML 資料流的陣列。</span><span class="sxs-lookup"><span data-stu-id="3672e-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="3672e-109">陣列可能是空的。</span><span class="sxs-lookup"><span data-stu-id="3672e-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3672e-110">備註</span><span class="sxs-lookup"><span data-stu-id="3672e-110">Remarks</span></span>  
 <span data-ttu-id="3672e-111">`GetXML`方法可能會影響效能，相關聯的 XML 資料流的大小而定。</span><span class="sxs-lookup"><span data-stu-id="3672e-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3672e-112">需求</span><span class="sxs-lookup"><span data-stu-id="3672e-112">Requirements</span></span>  
 <span data-ttu-id="3672e-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3672e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3672e-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3672e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3672e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3672e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3672e-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3672e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3672e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3672e-117">See Also</span></span>  
 [<span data-ttu-id="3672e-118">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="3672e-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="3672e-119">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="3672e-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
