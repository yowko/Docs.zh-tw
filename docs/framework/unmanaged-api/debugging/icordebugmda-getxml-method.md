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
ms.openlocfilehash: 9a088c7e4e9c72c8247ccdd384bc724587210c37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710866"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="5a04d-102">ICorDebugMDA::GetXML 方法</span><span class="sxs-lookup"><span data-stu-id="5a04d-102">ICorDebugMDA::GetXML Method</span></span>

<span data-ttu-id="5a04d-103">取得與 managed 偵錯工具相關聯的完整 XML 資料流程 (MDA) 以 [ICorDebugMDA](icordebugmda-interface.md)表示。</span><span class="sxs-lookup"><span data-stu-id="5a04d-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a04d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a04d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a04d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a04d-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="5a04d-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="5a04d-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5a04d-107">擴展XML 資料流程長度的指標。</span><span class="sxs-lookup"><span data-stu-id="5a04d-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="5a04d-108">擴展要在其中儲存 XML 資料流程的陣列。</span><span class="sxs-lookup"><span data-stu-id="5a04d-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="5a04d-109">陣列可能是空的。</span><span class="sxs-lookup"><span data-stu-id="5a04d-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a04d-110">備註</span><span class="sxs-lookup"><span data-stu-id="5a04d-110">Remarks</span></span>  

 <span data-ttu-id="5a04d-111">`GetXML`根據相關聯 XML 資料流程的大小而定，此方法可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="5a04d-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a04d-112">需求</span><span class="sxs-lookup"><span data-stu-id="5a04d-112">Requirements</span></span>  

 <span data-ttu-id="5a04d-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a04d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a04d-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a04d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a04d-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a04d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a04d-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a04d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a04d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a04d-117">See also</span></span>

- [<span data-ttu-id="5a04d-118">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="5a04d-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="5a04d-119">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="5a04d-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
