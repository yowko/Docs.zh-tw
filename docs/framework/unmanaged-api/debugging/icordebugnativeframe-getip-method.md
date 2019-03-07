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
ms.openlocfilehash: 3cac53ba77f04141d8d36b270226e97c292399eb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482726"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="64bb7-102">ICorDebugNativeFrame::GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="64bb7-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="64bb7-103">取得原生程式碼位移指令指標目前設定的位置。</span><span class="sxs-lookup"><span data-stu-id="64bb7-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64bb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="64bb7-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64bb7-105">參數</span><span class="sxs-lookup"><span data-stu-id="64bb7-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="64bb7-106">[out]在原生程式碼中的位移位置指標。</span><span class="sxs-lookup"><span data-stu-id="64bb7-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64bb7-107">備註</span><span class="sxs-lookup"><span data-stu-id="64bb7-107">Remarks</span></span>  
 <span data-ttu-id="64bb7-108">如果這個 「 ICorDebugNativeFrame"所表示的堆疊框架正在使用時，此位移為要執行的下一個指令的位址。</span><span class="sxs-lookup"><span data-stu-id="64bb7-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="64bb7-109">如果此堆疊框架不是作用中，此位移為下一個堆疊框架就會重新啟動時要執行指令的位址。</span><span class="sxs-lookup"><span data-stu-id="64bb7-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64bb7-110">需求</span><span class="sxs-lookup"><span data-stu-id="64bb7-110">Requirements</span></span>  
 <span data-ttu-id="64bb7-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64bb7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64bb7-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64bb7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64bb7-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64bb7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64bb7-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64bb7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64bb7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64bb7-115">See also</span></span>

