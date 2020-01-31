---
title: ICorDebug::Terminate 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 2d3f8360a1fb1164fd4e26f85246251409bee376
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788954"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="7a1f0-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="7a1f0-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="7a1f0-103">終止 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="7a1f0-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a1f0-104">在針對所有正在進行調試的進程收到[ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md)回呼之前，不應呼叫 `Terminate`。</span><span class="sxs-lookup"><span data-stu-id="7a1f0-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a1f0-105">語法</span><span class="sxs-lookup"><span data-stu-id="7a1f0-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7a1f0-106">備註</span><span class="sxs-lookup"><span data-stu-id="7a1f0-106">Remarks</span></span>  
 <span data-ttu-id="7a1f0-107">當不再需要 `ICorDebug` 物件時，必須呼叫 `Terminate`。</span><span class="sxs-lookup"><span data-stu-id="7a1f0-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a1f0-108">需求</span><span class="sxs-lookup"><span data-stu-id="7a1f0-108">Requirements</span></span>  
 <span data-ttu-id="7a1f0-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a1f0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a1f0-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a1f0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a1f0-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a1f0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a1f0-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a1f0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1f0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a1f0-113">See also</span></span>

- [<span data-ttu-id="7a1f0-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="7a1f0-114">ICorDebug Interface</span></span>](icordebug-interface.md)
