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
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139383"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="32170-102">ICorDebugProcess::IsTransitionStub 方法</span><span class="sxs-lookup"><span data-stu-id="32170-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="32170-103">取得值，指出位址是否在將導致轉換成 managed 程式碼的存根內部。</span><span class="sxs-lookup"><span data-stu-id="32170-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32170-104">語法</span><span class="sxs-lookup"><span data-stu-id="32170-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32170-105">參數</span><span class="sxs-lookup"><span data-stu-id="32170-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="32170-106">在指定有問題之位址的 `CORDB_ADDRESS` 值。</span><span class="sxs-lookup"><span data-stu-id="32170-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="32170-107">脫銷布林值的指標，如果指定的位址位於會導致轉換成 managed 程式碼的存根內部，則為 `true`：否則，會 `false``pbTransitionStub`。</span><span class="sxs-lookup"><span data-stu-id="32170-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32170-108">備註</span><span class="sxs-lookup"><span data-stu-id="32170-108">Remarks</span></span>  
 <span data-ttu-id="32170-109">未受管理的逐步執行程式碼可以使用 `IsTransitionStub` 方法，決定何時要將逐步執行控制傳回給 managed 分檔器。</span><span class="sxs-lookup"><span data-stu-id="32170-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="32170-110">您也可以查看可移植執行檔（PE）檔案中的資訊，以識別轉換存根。</span><span class="sxs-lookup"><span data-stu-id="32170-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32170-111">需求</span><span class="sxs-lookup"><span data-stu-id="32170-111">Requirements</span></span>  
 <span data-ttu-id="32170-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32170-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32170-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32170-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32170-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32170-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32170-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32170-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
