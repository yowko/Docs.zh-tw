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
ms.openlocfilehash: d234e01e3d47a64b9a001591ee2b61074eea8afb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403389"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="ae857-102">ICorDebugClass2::SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="ae857-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="ae857-103">每個類別的方法設定值，指出方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae857-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae857-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae857-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae857-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae857-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="ae857-106">[in]設定為`true`表示方法是由使用者定義程式碼，否則設為`false`。</span><span class="sxs-lookup"><span data-stu-id="ae857-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae857-107">備註</span><span class="sxs-lookup"><span data-stu-id="ae857-107">Remarks</span></span>  
 <span data-ttu-id="ae857-108">剛-我的程式碼 (JMC) stepper 將略過的非使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae857-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="ae857-109">使用者定義的程式碼必須是可偵錯的程式碼的子集。</span><span class="sxs-lookup"><span data-stu-id="ae857-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="ae857-110">`SetJMCStatus` 如果無法設定的值對於任何方法，即使它已成功設定的值為所有其他方法會傳回 S_FALSE 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="ae857-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae857-111">需求</span><span class="sxs-lookup"><span data-stu-id="ae857-111">Requirements</span></span>  
 <span data-ttu-id="ae857-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae857-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae857-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae857-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae857-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae857-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae857-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae857-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
