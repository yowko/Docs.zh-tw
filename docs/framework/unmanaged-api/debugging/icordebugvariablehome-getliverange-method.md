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
ms.openlocfilehash: 28e41106ffcaf1ed2ed87166e641bb5e5f447e47
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791021"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="ca01d-102">IcorDebugVariableHome：： GetLiveRange 方法</span><span class="sxs-lookup"><span data-stu-id="ca01d-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="ca01d-103">取得此變數所在的原生範圍。</span><span class="sxs-lookup"><span data-stu-id="ca01d-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca01d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca01d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca01d-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca01d-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="ca01d-106">脫銷變數第一次上線的邏輯位移。</span><span class="sxs-lookup"><span data-stu-id="ca01d-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="ca01d-107">脫銷緊接在變數上次存留位置之後的邏輯位移。</span><span class="sxs-lookup"><span data-stu-id="ca01d-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca01d-108">需求</span><span class="sxs-lookup"><span data-stu-id="ca01d-108">Requirements</span></span>  
 <span data-ttu-id="ca01d-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca01d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca01d-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca01d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca01d-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca01d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca01d-112">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca01d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca01d-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca01d-113">See also</span></span>

- [<span data-ttu-id="ca01d-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="ca01d-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
