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
ms.openlocfilehash: 516fcf8a97b92eac8dfff9eae34199caa97c2d2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710931"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="f63e1-102">ICorDebugMDA::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="f63e1-102">ICorDebugMDA::GetName Method</span></span>

<span data-ttu-id="f63e1-103">取得字串，其中包含 [ICorDebugMDA](icordebugmda-interface.md)所代表之 managed 偵錯工具 (MDA) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="f63e1-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="f63e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f63e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="f63e1-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="f63e1-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="f63e1-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f63e1-107">擴展名稱長度的指標。</span><span class="sxs-lookup"><span data-stu-id="f63e1-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="f63e1-108">擴展要在其中儲存名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="f63e1-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f63e1-109">備註</span><span class="sxs-lookup"><span data-stu-id="f63e1-109">Remarks</span></span>  

 <span data-ttu-id="f63e1-110">MDA 名稱是唯一的值。</span><span class="sxs-lookup"><span data-stu-id="f63e1-110">MDA names are unique values.</span></span> <span data-ttu-id="f63e1-111">`GetName`方法是一個方便的效能替代方法，可讓您從資料流程中取得 XML 資料流程，並根據架構將名稱解壓縮。</span><span class="sxs-lookup"><span data-stu-id="f63e1-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f63e1-112">需求</span><span class="sxs-lookup"><span data-stu-id="f63e1-112">Requirements</span></span>  

 <span data-ttu-id="f63e1-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f63e1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f63e1-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f63e1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f63e1-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f63e1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f63e1-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f63e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63e1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f63e1-117">See also</span></span>

- [<span data-ttu-id="f63e1-118">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="f63e1-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="f63e1-119">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="f63e1-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
