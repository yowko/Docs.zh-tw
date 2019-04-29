---
title: ICorDebugProcess::IsTransitionStub 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18084cb69d2c620fc892cc05e5a561e8fda3bc1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775514"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="45404-102">ICorDebugProcess::IsTransitionStub 方法</span><span class="sxs-lookup"><span data-stu-id="45404-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="45404-103">取得值，指出位址是否會導致轉換到 managed 程式碼的虛設常式內。</span><span class="sxs-lookup"><span data-stu-id="45404-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45404-104">語法</span><span class="sxs-lookup"><span data-stu-id="45404-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45404-105">參數</span><span class="sxs-lookup"><span data-stu-id="45404-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="45404-106">[in]A`CORDB_ADDRESS`值，指定的位址。</span><span class="sxs-lookup"><span data-stu-id="45404-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="45404-107">[out]布林值的指標`true`如果指定的位址位於虛設常式，會導致轉換到 managed 程式碼; 否則 \*`pbTransitionStub`是`false`。</span><span class="sxs-lookup"><span data-stu-id="45404-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45404-108">備註</span><span class="sxs-lookup"><span data-stu-id="45404-108">Remarks</span></span>  
 <span data-ttu-id="45404-109">`IsTransitionStub`方法可以由未受管理的逐步執行程式碼用來決定何時要將逐步執行控制權傳回給受管理的步進。</span><span class="sxs-lookup"><span data-stu-id="45404-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="45404-110">您也可以查看在可攜式執行檔 (PE) 中的資訊識別轉換虛設常式。</span><span class="sxs-lookup"><span data-stu-id="45404-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45404-111">需求</span><span class="sxs-lookup"><span data-stu-id="45404-111">Requirements</span></span>  
 <span data-ttu-id="45404-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45404-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45404-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45404-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45404-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45404-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45404-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45404-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
