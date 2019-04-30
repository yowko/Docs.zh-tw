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
ms.openlocfilehash: 82902e6a395fe62464065ccea4cca5b52c960f0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988808"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="8b883-102">ICorDebugFrame::GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="8b883-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="8b883-103">取得在目前的鏈結中，呼叫此框架 ICorDebugFrame 物件指標。</span><span class="sxs-lookup"><span data-stu-id="8b883-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b883-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b883-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b883-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b883-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="8b883-106">[out]位址指標`ICorDebugFrame`物件，表示呼叫端的框架。</span><span class="sxs-lookup"><span data-stu-id="8b883-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="8b883-107">此值為 null 如果被呼叫的框架是目前的鏈結中最外層的框架。</span><span class="sxs-lookup"><span data-stu-id="8b883-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b883-108">需求</span><span class="sxs-lookup"><span data-stu-id="8b883-108">Requirements</span></span>  
 <span data-ttu-id="8b883-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b883-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b883-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b883-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b883-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b883-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b883-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b883-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
