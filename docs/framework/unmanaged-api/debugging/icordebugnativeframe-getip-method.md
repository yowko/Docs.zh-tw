---
title: ICorDebugNativeFrame::GetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e9149bafc866f89253c4318ac69f2705431e48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765299"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="39cd4-102">ICorDebugNativeFrame::GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="39cd4-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="39cd4-103">取得原生程式碼位移指令指標目前設定的位置。</span><span class="sxs-lookup"><span data-stu-id="39cd4-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39cd4-104">語法</span><span class="sxs-lookup"><span data-stu-id="39cd4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39cd4-105">參數</span><span class="sxs-lookup"><span data-stu-id="39cd4-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="39cd4-106">[out]在原生程式碼中的位移位置指標。</span><span class="sxs-lookup"><span data-stu-id="39cd4-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39cd4-107">備註</span><span class="sxs-lookup"><span data-stu-id="39cd4-107">Remarks</span></span>  
 <span data-ttu-id="39cd4-108">如果這個 「 ICorDebugNativeFrame"所表示的堆疊框架正在使用時，此位移為要執行的下一個指令的位址。</span><span class="sxs-lookup"><span data-stu-id="39cd4-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="39cd4-109">如果此堆疊框架不是作用中，此位移為下一個堆疊框架就會重新啟動時要執行指令的位址。</span><span class="sxs-lookup"><span data-stu-id="39cd4-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39cd4-110">需求</span><span class="sxs-lookup"><span data-stu-id="39cd4-110">Requirements</span></span>  
 <span data-ttu-id="39cd4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39cd4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39cd4-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39cd4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39cd4-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39cd4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39cd4-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39cd4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39cd4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39cd4-115">See also</span></span>
