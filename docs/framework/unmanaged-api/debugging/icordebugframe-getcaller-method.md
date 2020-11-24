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
ms.openlocfilehash: b52499e509bf172b03b5e4d2b1e4c677dc800281
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690469"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="c5565-102">ICorDebugFrame::GetCaller 方法</span><span class="sxs-lookup"><span data-stu-id="c5565-102">ICorDebugFrame::GetCaller Method</span></span>

<span data-ttu-id="c5565-103">取得目前鏈中呼叫此框架之 ICorDebugFrame 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="c5565-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5565-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5565-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5565-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5565-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="c5565-106">擴展物件位址的指標 `ICorDebugFrame` ，該物件表示呼叫的框架。</span><span class="sxs-lookup"><span data-stu-id="c5565-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="c5565-107">如果所呼叫的框架是目前鏈中的最外層框架，則此值為 null。</span><span class="sxs-lookup"><span data-stu-id="c5565-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5565-108">需求</span><span class="sxs-lookup"><span data-stu-id="c5565-108">Requirements</span></span>  

 <span data-ttu-id="c5565-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5565-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5565-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5565-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5565-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5565-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5565-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5565-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
