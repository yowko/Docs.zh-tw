---
title: ICorDebugClass2::SetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
ms.openlocfilehash: a862dd3f6a9c10c6b3a5a0bb41208d351c4ca9f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125696"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="df3db-102">ICorDebugClass2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="df3db-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="df3db-103">針對類別的每個方法，設定一個值，指出此方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="df3db-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df3db-104">語法</span><span class="sxs-lookup"><span data-stu-id="df3db-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df3db-105">參數</span><span class="sxs-lookup"><span data-stu-id="df3db-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="df3db-106">在設定為 `true`，表示該方法是使用者定義的程式碼;否則，請將設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="df3db-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df3db-107">備註</span><span class="sxs-lookup"><span data-stu-id="df3db-107">Remarks</span></span>  
 <span data-ttu-id="df3db-108">只有 my code （JMC）分檔器會略過非使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="df3db-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="df3db-109">使用者定義的程式碼必須是可偵錯工具代碼的子集。</span><span class="sxs-lookup"><span data-stu-id="df3db-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="df3db-110">如果不能設定任何方法的值，則 `SetJMCStatus` 會傳回值為 S_FALSE 的 HRESULT，即使它成功設定所有其他方法的值也一樣。</span><span class="sxs-lookup"><span data-stu-id="df3db-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df3db-111">需求</span><span class="sxs-lookup"><span data-stu-id="df3db-111">Requirements</span></span>  
 <span data-ttu-id="df3db-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df3db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df3db-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df3db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df3db-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df3db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df3db-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df3db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
