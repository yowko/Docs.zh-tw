---
title: IcorDebugVariableHome::GetLiveRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 894629b7cc1c48eb6c1820c65a0a2a41332a8080
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549687"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="e46ae-102">IcorDebugVariableHome::GetLiveRange 方法</span><span class="sxs-lookup"><span data-stu-id="e46ae-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="e46ae-103">取得原生的此變數是即時的範圍。</span><span class="sxs-lookup"><span data-stu-id="e46ae-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e46ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="e46ae-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e46ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="e46ae-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="e46ae-106">[out]變數是第一個即時邏輯位移。</span><span class="sxs-lookup"><span data-stu-id="e46ae-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="e46ae-107">[out]變數是最後一個即時點之後，立即邏輯的位移。</span><span class="sxs-lookup"><span data-stu-id="e46ae-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e46ae-108">需求</span><span class="sxs-lookup"><span data-stu-id="e46ae-108">Requirements</span></span>  
 <span data-ttu-id="e46ae-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e46ae-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e46ae-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e46ae-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e46ae-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e46ae-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e46ae-112">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e46ae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46ae-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e46ae-113">See also</span></span>
- [<span data-ttu-id="e46ae-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="e46ae-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
