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
ms.openlocfilehash: 1db2c9b5e65ae150f05242172f5ea16db433bbb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717821"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="46f62-102">ICorDebugClass2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="46f62-102">ICorDebugClass2::SetJMCStatus Method</span></span>

<span data-ttu-id="46f62-103">針對類別的每個方法，設定一個值，指出方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="46f62-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f62-104">語法</span><span class="sxs-lookup"><span data-stu-id="46f62-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46f62-105">參數</span><span class="sxs-lookup"><span data-stu-id="46f62-105">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="46f62-106">在設定為， `true` 表示方法是使用者定義的程式碼，否則設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="46f62-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46f62-107">備註</span><span class="sxs-lookup"><span data-stu-id="46f62-107">Remarks</span></span>  

 <span data-ttu-id="46f62-108">My code (JMC) 的分檔器將會略過非使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="46f62-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="46f62-109">使用者定義的程式碼必須是可偵錯工具代碼的子集。</span><span class="sxs-lookup"><span data-stu-id="46f62-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="46f62-110">`SetJMCStatus` 如果無法設定任何方法的值，則會傳回 S_FALSE 的 HRESULT 值，即使它成功設定所有其他方法的值也是如此。</span><span class="sxs-lookup"><span data-stu-id="46f62-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46f62-111">需求</span><span class="sxs-lookup"><span data-stu-id="46f62-111">Requirements</span></span>  

 <span data-ttu-id="46f62-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46f62-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46f62-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46f62-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46f62-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46f62-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46f62-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46f62-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
