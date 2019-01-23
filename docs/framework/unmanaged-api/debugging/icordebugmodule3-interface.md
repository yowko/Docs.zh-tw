---
title: ICorDebugModule3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d504e694810bfa1b9f3258f75e307bfb60d4ad7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496802"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="64bf6-102">ICorDebugModule3 介面</span><span class="sxs-lookup"><span data-stu-id="64bf6-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="64bf6-103">建立動態模組的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="64bf6-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64bf6-104">語法</span><span class="sxs-lookup"><span data-stu-id="64bf6-104">Syntax</span></span>  
  
```  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="64bf6-105">方法</span><span class="sxs-lookup"><span data-stu-id="64bf6-105">Methods</span></span>  
  
|<span data-ttu-id="64bf6-106">方法</span><span class="sxs-lookup"><span data-stu-id="64bf6-106">Method</span></span>|<span data-ttu-id="64bf6-107">描述</span><span class="sxs-lookup"><span data-stu-id="64bf6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64bf6-108">ICorDebugModule3::CreateReaderForInMemorySymbols 方法</span><span class="sxs-lookup"><span data-stu-id="64bf6-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="64bf6-109">建立符號讀取器 (通常[ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) 的動態模組。</span><span class="sxs-lookup"><span data-stu-id="64bf6-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64bf6-110">備註</span><span class="sxs-lookup"><span data-stu-id="64bf6-110">Remarks</span></span>  
 <span data-ttu-id="64bf6-111">這個介面會以邏輯方式擴充的 」 ICorDebugModule"和"ICorDebugModule2"介面。</span><span class="sxs-lookup"><span data-stu-id="64bf6-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64bf6-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="64bf6-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64bf6-113">需求</span><span class="sxs-lookup"><span data-stu-id="64bf6-113">Requirements</span></span>  
 <span data-ttu-id="64bf6-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64bf6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64bf6-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64bf6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64bf6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64bf6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64bf6-117">**.NET framework 版本：** 4.5，4，3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="64bf6-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="64bf6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64bf6-118">See also</span></span>
- [<span data-ttu-id="64bf6-119">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="64bf6-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="64bf6-120">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="64bf6-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="64bf6-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="64bf6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
