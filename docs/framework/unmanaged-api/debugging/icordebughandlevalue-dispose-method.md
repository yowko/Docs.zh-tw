---
title: ICorDebugHandleValue::Dispose 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
ms.openlocfilehash: 957035591090fb5a6a615662c4840ff16509ee20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138498"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="7af2d-102">ICorDebugHandleValue::Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="7af2d-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="7af2d-103">釋放這個 ICorDebugHandleValue 物件所參考的控制碼，而不明確釋放介面指標。</span><span class="sxs-lookup"><span data-stu-id="7af2d-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7af2d-104">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="7af2d-105">需求</span><span class="sxs-lookup"><span data-stu-id="7af2d-105">Requirements</span></span>  
 <span data-ttu-id="7af2d-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7af2d-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7af2d-107">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7af2d-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7af2d-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7af2d-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7af2d-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7af2d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
