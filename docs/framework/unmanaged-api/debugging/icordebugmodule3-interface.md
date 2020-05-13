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
ms.openlocfilehash: 69fd3e2df4a4eafe91cc025f28e1387cc443ea04
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212304"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="c99d1-102">ICorDebugModule3 介面</span><span class="sxs-lookup"><span data-stu-id="c99d1-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="c99d1-103">建立動態模組的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="c99d1-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c99d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c99d1-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c99d1-105">方法</span><span class="sxs-lookup"><span data-stu-id="c99d1-105">Methods</span></span>  
  
|<span data-ttu-id="c99d1-106">方法</span><span class="sxs-lookup"><span data-stu-id="c99d1-106">Method</span></span>|<span data-ttu-id="c99d1-107">描述</span><span class="sxs-lookup"><span data-stu-id="c99d1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c99d1-108">ICorDebugModule3::CreateReaderForInMemorySymbols 方法</span><span class="sxs-lookup"><span data-stu-id="c99d1-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="c99d1-109">建立動態模組的符號讀取器（通常是[ISymUnmanagedReader 介面](../diagnostics/isymunmanagedreader-interface.md)）。</span><span class="sxs-lookup"><span data-stu-id="c99d1-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c99d1-110">備註</span><span class="sxs-lookup"><span data-stu-id="c99d1-110">Remarks</span></span>  
 <span data-ttu-id="c99d1-111">這個介面會以邏輯方式擴充 "ICorDebugModule" 和 "ICorDebugModule2" 介面。</span><span class="sxs-lookup"><span data-stu-id="c99d1-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c99d1-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c99d1-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c99d1-113">需求</span><span class="sxs-lookup"><span data-stu-id="c99d1-113">Requirements</span></span>  
 <span data-ttu-id="c99d1-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c99d1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c99d1-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c99d1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c99d1-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c99d1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c99d1-117">**.NET Framework 版本：** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c99d1-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c99d1-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="c99d1-118">See also</span></span>

- [<span data-ttu-id="c99d1-119">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="c99d1-119">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="c99d1-120">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="c99d1-120">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="c99d1-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c99d1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
