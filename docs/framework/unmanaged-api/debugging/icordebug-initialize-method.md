---
title: ICorDebug::Initialize 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: 3d27cf1987d7e9896885f87857554f4039c8d714
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788984"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="e53b5-102">ICorDebug::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="e53b5-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="e53b5-103">初始化 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="e53b5-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="e53b5-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e53b5-105">備註</span><span class="sxs-lookup"><span data-stu-id="e53b5-105">Remarks</span></span>  
 <span data-ttu-id="e53b5-106">偵錯工具在建立時必須呼叫 `Initialize`，以初始化偵錯工具服務。</span><span class="sxs-lookup"><span data-stu-id="e53b5-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="e53b5-107">您必須先呼叫這個方法，才能呼叫 `ICorDebug` 上的任何其他方法。</span><span class="sxs-lookup"><span data-stu-id="e53b5-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e53b5-108">需求</span><span class="sxs-lookup"><span data-stu-id="e53b5-108">Requirements</span></span>  
 <span data-ttu-id="e53b5-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e53b5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e53b5-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e53b5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e53b5-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e53b5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e53b5-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e53b5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53b5-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="e53b5-113">See also</span></span>

- [<span data-ttu-id="e53b5-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="e53b5-114">ICorDebug Interface</span></span>](icordebug-interface.md)
