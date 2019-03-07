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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a179b68e2196eeadc712ae8f7d023b2943533335
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471065"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="4ec66-102">ICorDebugFrame::GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="4ec66-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="4ec66-103">取得目前此框架呼叫鏈結中 ICorDebugFrame 物件指標。</span><span class="sxs-lookup"><span data-stu-id="4ec66-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec66-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ec66-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ec66-105">參數</span><span class="sxs-lookup"><span data-stu-id="4ec66-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="4ec66-106">[out]位址指標`ICorDebugFrame`物件，表示被呼叫的框架。</span><span class="sxs-lookup"><span data-stu-id="4ec66-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="4ec66-107">這個值是 null，如果呼叫端的框架是目前的鏈結中最內層的框架。</span><span class="sxs-lookup"><span data-stu-id="4ec66-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec66-108">需求</span><span class="sxs-lookup"><span data-stu-id="4ec66-108">Requirements</span></span>  
 <span data-ttu-id="4ec66-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ec66-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ec66-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ec66-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ec66-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ec66-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ec66-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ec66-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
