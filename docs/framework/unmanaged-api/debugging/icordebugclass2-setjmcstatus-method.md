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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23f248625753c15a4798ea69a1eb3b377b79f95d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747760"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="e551c-102">ICorDebugClass2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="e551c-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="e551c-103">每一個方法的類別中，設定值，指出方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e551c-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e551c-104">語法</span><span class="sxs-lookup"><span data-stu-id="e551c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e551c-105">參數</span><span class="sxs-lookup"><span data-stu-id="e551c-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="e551c-106">[in]設定為`true`表示的方法是使用者定義程式碼; 否則設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="e551c-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e551c-107">備註</span><span class="sxs-lookup"><span data-stu-id="e551c-107">Remarks</span></span>  
 <span data-ttu-id="e551c-108">只是我的程式碼 (JMC) 步進會略過的非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="e551c-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="e551c-109">使用者定義的程式碼必須是可偵錯的程式碼的子集。</span><span class="sxs-lookup"><span data-stu-id="e551c-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="e551c-110">`SetJMCStatus` 如果它無法設定值，對於任何方法，即使它已成功設定所有其他方法的值，則傳回 S_FALSE 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="e551c-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e551c-111">需求</span><span class="sxs-lookup"><span data-stu-id="e551c-111">Requirements</span></span>  
 <span data-ttu-id="e551c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e551c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e551c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e551c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e551c-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e551c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e551c-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e551c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
