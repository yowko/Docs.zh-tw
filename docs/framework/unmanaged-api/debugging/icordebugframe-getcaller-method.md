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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a637cebb9e1aef20c600353eb14fe900ad7513c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754167"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="ffe2c-102">ICorDebugFrame::GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="ffe2c-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="ffe2c-103">取得在目前的鏈結中，呼叫此框架 ICorDebugFrame 物件指標。</span><span class="sxs-lookup"><span data-stu-id="ffe2c-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe2c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ffe2c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffe2c-105">參數</span><span class="sxs-lookup"><span data-stu-id="ffe2c-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="ffe2c-106">[out]位址指標`ICorDebugFrame`物件，表示呼叫端的框架。</span><span class="sxs-lookup"><span data-stu-id="ffe2c-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="ffe2c-107">此值為 null 如果被呼叫的框架是目前的鏈結中最外層的框架。</span><span class="sxs-lookup"><span data-stu-id="ffe2c-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe2c-108">需求</span><span class="sxs-lookup"><span data-stu-id="ffe2c-108">Requirements</span></span>  
 <span data-ttu-id="ffe2c-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ffe2c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffe2c-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffe2c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffe2c-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffe2c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffe2c-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffe2c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
