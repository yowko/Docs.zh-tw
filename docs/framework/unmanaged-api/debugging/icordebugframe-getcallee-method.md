---
title: ICorDebugFrame::GetCallee 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: b83dec65e1dd4fc610be3190e8126e6d9d38a6e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121228"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="9c97f-102">ICorDebugFrame::GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="9c97f-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="9c97f-103">取得此框架所呼叫之目前鏈中 ICorDebugFrame 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="9c97f-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c97f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c97f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c97f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c97f-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="9c97f-106">脫銷表示所呼叫之框架的 `ICorDebugFrame` 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="9c97f-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="9c97f-107">如果呼叫框架是目前鏈中最內層的框架，則此值為 null。</span><span class="sxs-lookup"><span data-stu-id="9c97f-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c97f-108">需求</span><span class="sxs-lookup"><span data-stu-id="9c97f-108">Requirements</span></span>  
 <span data-ttu-id="9c97f-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c97f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c97f-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c97f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c97f-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c97f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c97f-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c97f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
