---
title: ICorDebugFrame::GetCaller 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: 843399b7e3de522e2c4574963897430aa60a5a50
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114800"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="2d984-102">ICorDebugFrame::GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="2d984-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="2d984-103">取得目前鏈中呼叫此框架之 ICorDebugFrame 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="2d984-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d984-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d984-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d984-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d984-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="2d984-106">脫銷表示呼叫框架之 `ICorDebugFrame` 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="2d984-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="2d984-107">如果被呼叫的框架是目前鏈中的最外層框架，則此值為 null。</span><span class="sxs-lookup"><span data-stu-id="2d984-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d984-108">需求</span><span class="sxs-lookup"><span data-stu-id="2d984-108">Requirements</span></span>  
 <span data-ttu-id="2d984-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d984-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d984-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d984-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d984-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d984-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d984-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d984-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
