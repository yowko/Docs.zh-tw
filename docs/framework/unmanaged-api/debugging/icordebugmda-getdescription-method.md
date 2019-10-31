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
ms.openlocfilehash: bfe77982b88b2fc96dc2846b9db04df28bfc0c38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131441"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="c1b71-102">ICorDebugMDA::GetDescription 方法</span><span class="sxs-lookup"><span data-stu-id="c1b71-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="c1b71-103">取得字串，其中包含[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)所代表的 managed 偵錯工具（MDA）的描述。</span><span class="sxs-lookup"><span data-stu-id="c1b71-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b71-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1b71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1b71-105">參數</span><span class="sxs-lookup"><span data-stu-id="c1b71-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c1b71-106">在將儲存描述的字串緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="c1b71-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c1b71-107">脫銷字串緩衝區中傳回之位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="c1b71-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="c1b71-108">脫銷包含 MDA 描述的字串緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c1b71-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1b71-109">備註</span><span class="sxs-lookup"><span data-stu-id="c1b71-109">Remarks</span></span>  
 <span data-ttu-id="c1b71-110">字串的長度可以是零。</span><span class="sxs-lookup"><span data-stu-id="c1b71-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1b71-111">需求</span><span class="sxs-lookup"><span data-stu-id="c1b71-111">Requirements</span></span>  
 <span data-ttu-id="c1b71-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1b71-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b71-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1b71-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1b71-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1b71-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1b71-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b71-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b71-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1b71-116">See also</span></span>

- [<span data-ttu-id="c1b71-117">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="c1b71-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="c1b71-118">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="c1b71-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
