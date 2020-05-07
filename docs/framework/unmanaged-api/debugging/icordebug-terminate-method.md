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
ms.openlocfilehash: 44bb98f54debb129f951cc388fea81ca0f17b20c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895313"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="53d4d-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="53d4d-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="53d4d-103">終止`ICorDebug`物件。</span><span class="sxs-lookup"><span data-stu-id="53d4d-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53d4d-104">`Terminate`必須等到針對所有正在進行調試的進程收到[ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md)回呼之後，才能呼叫。</span><span class="sxs-lookup"><span data-stu-id="53d4d-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53d4d-105">語法</span><span class="sxs-lookup"><span data-stu-id="53d4d-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="53d4d-106">備註</span><span class="sxs-lookup"><span data-stu-id="53d4d-106">Remarks</span></span>  
 <span data-ttu-id="53d4d-107">`Terminate`當不再需要物件時`ICorDebug` ，必須呼叫。</span><span class="sxs-lookup"><span data-stu-id="53d4d-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53d4d-108">需求</span><span class="sxs-lookup"><span data-stu-id="53d4d-108">Requirements</span></span>  
 <span data-ttu-id="53d4d-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53d4d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53d4d-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53d4d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53d4d-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53d4d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53d4d-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53d4d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d4d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53d4d-113">See also</span></span>

- [<span data-ttu-id="53d4d-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="53d4d-114">ICorDebug Interface</span></span>](icordebug-interface.md)
