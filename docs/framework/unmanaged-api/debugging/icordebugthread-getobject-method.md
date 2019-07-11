---
title: ICorDebugThread::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3695f150797e6a59a2fb1d58c99f233a35d687ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771842"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="da8a4-102">ICorDebugThread::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="da8a4-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="da8a4-103">取得 common language runtime (CLR) 執行緒的介面指標。</span><span class="sxs-lookup"><span data-stu-id="da8a4-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da8a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="da8a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da8a4-105">參數</span><span class="sxs-lookup"><span data-stu-id="da8a4-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="da8a4-106">[out]ICorDebugValue 介面物件，表示 CLR 執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="da8a4-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da8a4-107">需求</span><span class="sxs-lookup"><span data-stu-id="da8a4-107">Requirements</span></span>  
 <span data-ttu-id="da8a4-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da8a4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da8a4-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da8a4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da8a4-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da8a4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da8a4-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da8a4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da8a4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da8a4-112">See also</span></span>

- <xref:System.Threading.Thread>
