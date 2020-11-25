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
ms.openlocfilehash: 4d66d09e02b907281f64400b0c605a7b5c44d476
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731042"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="84588-102">IcorDebugVariableHome：： GetLiveRange 方法</span><span class="sxs-lookup"><span data-stu-id="84588-102">IcorDebugVariableHome::GetLiveRange Method</span></span>

<span data-ttu-id="84588-103">取得這個變數的存留原生範圍。</span><span class="sxs-lookup"><span data-stu-id="84588-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84588-104">語法</span><span class="sxs-lookup"><span data-stu-id="84588-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84588-105">參數</span><span class="sxs-lookup"><span data-stu-id="84588-105">Parameters</span></span>  

 `pStartOffset`  
 <span data-ttu-id="84588-106">擴展變數第一次存留的邏輯位移。</span><span class="sxs-lookup"><span data-stu-id="84588-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="84588-107">擴展緊接在變數最後存留點之後的邏輯位移。</span><span class="sxs-lookup"><span data-stu-id="84588-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84588-108">需求</span><span class="sxs-lookup"><span data-stu-id="84588-108">Requirements</span></span>  

 <span data-ttu-id="84588-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84588-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84588-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84588-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84588-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84588-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84588-112">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84588-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84588-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84588-113">See also</span></span>

- [<span data-ttu-id="84588-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="84588-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
