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
ms.openlocfilehash: 6ed6570e11008e52d4b1f97c2dc90e2ccbef2e35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750614"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="3f7fc-102">ICorDebugClass2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="3f7fc-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="3f7fc-103">每一個方法的類別中，設定值，指出方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3f7fc-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f7fc-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f7fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="3f7fc-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="3f7fc-106">[in]設定為`true`表示的方法是使用者定義程式碼; 否則設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="3f7fc-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f7fc-107">備註</span><span class="sxs-lookup"><span data-stu-id="3f7fc-107">Remarks</span></span>  
 <span data-ttu-id="3f7fc-108">只是我的程式碼 (JMC) 步進會略過的非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="3f7fc-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="3f7fc-109">使用者定義的程式碼必須是可偵錯的程式碼的子集。</span><span class="sxs-lookup"><span data-stu-id="3f7fc-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="3f7fc-110">`SetJMCStatus` 如果它無法設定值，對於任何方法，即使它已成功設定所有其他方法的值，則傳回 S_FALSE 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="3f7fc-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7fc-111">需求</span><span class="sxs-lookup"><span data-stu-id="3f7fc-111">Requirements</span></span>  
 <span data-ttu-id="3f7fc-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f7fc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f7fc-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f7fc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f7fc-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f7fc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f7fc-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f7fc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
