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
ms.openlocfilehash: 219aa27296dffa525bf3e2b836825437a8ce77b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207648"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="bcecd-102">ICorDebugMDA::GetXML 方法</span><span class="sxs-lookup"><span data-stu-id="bcecd-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="bcecd-103">取得與[ICorDebugMDA](icordebugmda-interface.md)代表的 managed 偵錯工具（MDA）相關聯的完整 XML 資料流程。</span><span class="sxs-lookup"><span data-stu-id="bcecd-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcecd-104">語法</span><span class="sxs-lookup"><span data-stu-id="bcecd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcecd-105">參數</span><span class="sxs-lookup"><span data-stu-id="bcecd-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="bcecd-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="bcecd-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bcecd-107">脫銷XML 資料流程長度的指標。</span><span class="sxs-lookup"><span data-stu-id="bcecd-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="bcecd-108">脫銷要在其中儲存 XML 資料流程的陣列。</span><span class="sxs-lookup"><span data-stu-id="bcecd-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="bcecd-109">陣列可能是空的。</span><span class="sxs-lookup"><span data-stu-id="bcecd-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcecd-110">備註</span><span class="sxs-lookup"><span data-stu-id="bcecd-110">Remarks</span></span>  
 <span data-ttu-id="bcecd-111">`GetXML`根據相關聯的 XML 資料流程大小而定，此方法可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="bcecd-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcecd-112">需求</span><span class="sxs-lookup"><span data-stu-id="bcecd-112">Requirements</span></span>  
 <span data-ttu-id="bcecd-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bcecd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcecd-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcecd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcecd-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcecd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcecd-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcecd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcecd-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="bcecd-117">See also</span></span>

- [<span data-ttu-id="bcecd-118">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="bcecd-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="bcecd-119">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="bcecd-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
