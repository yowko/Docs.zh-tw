---
title: IcorDebugVariableHome：： GetLiveRange 方法
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
ms.openlocfilehash: a8b8955d2f4c164031974f0d9021fb766ff2c030
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125120"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="caaee-102">IcorDebugVariableHome：： GetLiveRange 方法</span><span class="sxs-lookup"><span data-stu-id="caaee-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="caaee-103">取得此變數所在的原生範圍。</span><span class="sxs-lookup"><span data-stu-id="caaee-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caaee-104">語法</span><span class="sxs-lookup"><span data-stu-id="caaee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caaee-105">參數</span><span class="sxs-lookup"><span data-stu-id="caaee-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="caaee-106">脫銷變數第一次上線的邏輯位移。</span><span class="sxs-lookup"><span data-stu-id="caaee-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="caaee-107">脫銷緊接在變數上次存留位置之後的邏輯位移。</span><span class="sxs-lookup"><span data-stu-id="caaee-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caaee-108">需求</span><span class="sxs-lookup"><span data-stu-id="caaee-108">Requirements</span></span>  
 <span data-ttu-id="caaee-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="caaee-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caaee-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="caaee-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="caaee-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="caaee-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caaee-112">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caaee-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caaee-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="caaee-113">See also</span></span>

- [<span data-ttu-id="caaee-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="caaee-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
