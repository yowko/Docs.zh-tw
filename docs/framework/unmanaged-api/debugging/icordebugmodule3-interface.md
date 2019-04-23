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
ms.openlocfilehash: a340086be042c790ae7bf750759ff80f7c9eaf23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122612"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="8296b-102">ICorDebugModule3 介面</span><span class="sxs-lookup"><span data-stu-id="8296b-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="8296b-103">建立動態模組的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="8296b-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8296b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8296b-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8296b-105">方法</span><span class="sxs-lookup"><span data-stu-id="8296b-105">Methods</span></span>  
  
|<span data-ttu-id="8296b-106">方法</span><span class="sxs-lookup"><span data-stu-id="8296b-106">Method</span></span>|<span data-ttu-id="8296b-107">描述</span><span class="sxs-lookup"><span data-stu-id="8296b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8296b-108">ICorDebugModule3::CreateReaderForInMemorySymbols 方法</span><span class="sxs-lookup"><span data-stu-id="8296b-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="8296b-109">建立符號讀取器 (通常[ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) 的動態模組。</span><span class="sxs-lookup"><span data-stu-id="8296b-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8296b-110">備註</span><span class="sxs-lookup"><span data-stu-id="8296b-110">Remarks</span></span>  
 <span data-ttu-id="8296b-111">這個介面會以邏輯方式擴充的 」 ICorDebugModule"和"ICorDebugModule2"介面。</span><span class="sxs-lookup"><span data-stu-id="8296b-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8296b-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8296b-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8296b-113">需求</span><span class="sxs-lookup"><span data-stu-id="8296b-113">Requirements</span></span>  
 <span data-ttu-id="8296b-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8296b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8296b-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8296b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8296b-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8296b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8296b-117">**.NET framework 版本：** 4.5，4，3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="8296b-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8296b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8296b-118">See also</span></span>

- [<span data-ttu-id="8296b-119">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="8296b-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="8296b-120">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="8296b-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="8296b-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8296b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
