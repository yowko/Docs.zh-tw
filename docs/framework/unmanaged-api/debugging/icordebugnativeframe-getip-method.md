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
ms.openlocfilehash: 53576ca938074fb7e5974a96bb53a84cb6ed67ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213591"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="07733-102">ICorDebugNativeFrame::GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="07733-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="07733-103">取得目前設定指令指標的原生程式碼位移位置。</span><span class="sxs-lookup"><span data-stu-id="07733-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07733-104">語法</span><span class="sxs-lookup"><span data-stu-id="07733-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07733-105">參數</span><span class="sxs-lookup"><span data-stu-id="07733-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="07733-106">脫銷機器碼中位移位置的指標。</span><span class="sxs-lookup"><span data-stu-id="07733-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07733-107">備註</span><span class="sxs-lookup"><span data-stu-id="07733-107">Remarks</span></span>  
 <span data-ttu-id="07733-108">如果這個 "ICorDebugNativeFrame" 所代表的堆疊框架是作用中，則位移就是下一個要執行之指令的位址。</span><span class="sxs-lookup"><span data-stu-id="07733-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="07733-109">如果這個堆疊框架不在作用中，則位移是重新開機堆疊框架時，要執行的下一個指令的位址。</span><span class="sxs-lookup"><span data-stu-id="07733-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07733-110">需求</span><span class="sxs-lookup"><span data-stu-id="07733-110">Requirements</span></span>  
 <span data-ttu-id="07733-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07733-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07733-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07733-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07733-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07733-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07733-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07733-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07733-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07733-115">See also</span></span>
