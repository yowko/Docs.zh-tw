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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d21703aa911b5222fff71282e6da26aa5c0e2853
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756851"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="137e4-102">ICorDebugHandleValue::Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="137e4-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="137e4-103">釋放由這個 ICorDebugHandleValue 物件參考未明確地釋放介面指標控制代碼。</span><span class="sxs-lookup"><span data-stu-id="137e4-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="137e4-104">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="137e4-105">需求</span><span class="sxs-lookup"><span data-stu-id="137e4-105">Requirements</span></span>  
 <span data-ttu-id="137e4-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="137e4-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="137e4-107">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="137e4-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="137e4-108">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="137e4-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="137e4-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="137e4-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
