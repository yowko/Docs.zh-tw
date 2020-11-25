---
title: ICorDebugThread::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: d3697bd8a3f32c802ab2e335f89c84efaf3e4db0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727987"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="8e6c9-102">ICorDebugThread::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="8e6c9-102">ICorDebugThread::GetProcess Method</span></span>

<span data-ttu-id="8e6c9-103">取得這個 ICorDebugThread 形成元件之進程的介面指標。</span><span class="sxs-lookup"><span data-stu-id="8e6c9-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e6c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e6c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e6c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e6c9-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="8e6c9-106">擴展代表進程之 ICorDebugProcess 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="8e6c9-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e6c9-107">需求</span><span class="sxs-lookup"><span data-stu-id="8e6c9-107">Requirements</span></span>  

 <span data-ttu-id="8e6c9-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e6c9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e6c9-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e6c9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e6c9-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e6c9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e6c9-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e6c9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
