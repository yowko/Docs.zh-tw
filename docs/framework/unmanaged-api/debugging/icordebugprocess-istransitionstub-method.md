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
ms.openlocfilehash: ab2121605f974fdf3f9053214a4d29d8b0dd72db
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210696"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="b6269-102">ICorDebugProcess::IsTransitionStub 方法</span><span class="sxs-lookup"><span data-stu-id="b6269-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="b6269-103">取得值，指出位址是否在將導致轉換成 managed 程式碼的存根內部。</span><span class="sxs-lookup"><span data-stu-id="b6269-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6269-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6269-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6269-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6269-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b6269-106">在`CORDB_ADDRESS`值，指定有問題的位址。</span><span class="sxs-lookup"><span data-stu-id="b6269-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="b6269-107">脫銷布林值的指標， `true` 如果指定的位址位於會導致轉換成 managed 程式碼的存根內部，則為，否則為 \* `pbTransitionStub` `false` 。</span><span class="sxs-lookup"><span data-stu-id="b6269-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6269-108">備註</span><span class="sxs-lookup"><span data-stu-id="b6269-108">Remarks</span></span>  
 <span data-ttu-id="b6269-109">未受管理的 `IsTransitionStub` 逐步執行程式碼可以使用方法，決定何時要將逐步執行控制傳回給 managed 分檔器。</span><span class="sxs-lookup"><span data-stu-id="b6269-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="b6269-110">您也可以查看可移植執行檔（PE）檔案中的資訊，以識別轉換存根。</span><span class="sxs-lookup"><span data-stu-id="b6269-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6269-111">需求</span><span class="sxs-lookup"><span data-stu-id="b6269-111">Requirements</span></span>  
 <span data-ttu-id="b6269-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6269-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6269-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6269-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6269-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6269-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6269-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6269-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
