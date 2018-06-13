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
ms.openlocfilehash: c0f9c586a9e95fc2e57c4956601f6dce2b988159
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423061"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="446db-102">IcorDebugVariableHome::GetLiveRange 方法</span><span class="sxs-lookup"><span data-stu-id="446db-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="446db-103">取得原生的此變數是即時的範圍。</span><span class="sxs-lookup"><span data-stu-id="446db-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="446db-104">語法</span><span class="sxs-lookup"><span data-stu-id="446db-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="446db-105">參數</span><span class="sxs-lookup"><span data-stu-id="446db-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="446db-106">[out]變數在第一個即時邏輯的位移。</span><span class="sxs-lookup"><span data-stu-id="446db-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="446db-107">[out]變數在最後一個即時點之後，立即邏輯的位移。</span><span class="sxs-lookup"><span data-stu-id="446db-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="446db-108">需求</span><span class="sxs-lookup"><span data-stu-id="446db-108">Requirements</span></span>  
 <span data-ttu-id="446db-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="446db-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="446db-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="446db-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="446db-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="446db-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="446db-112">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="446db-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446db-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="446db-113">See Also</span></span>  
 [<span data-ttu-id="446db-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="446db-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
