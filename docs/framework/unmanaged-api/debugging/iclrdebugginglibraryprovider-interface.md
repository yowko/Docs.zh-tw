---
title: ICLRDebuggingLibraryProvider 介面
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9d851a31cbbf429f49b9f369ce9bc03fa110b5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731981"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="d2ade-102">ICLRDebuggingLibraryProvider 介面</span><span class="sxs-lookup"><span data-stu-id="d2ade-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="d2ade-103">包含[ProvideLibrary 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)方法，以取得程式庫提供者回呼介面，可讓通用語言執行階段版本特定偵錯程式庫尋找並載入需求。</span><span class="sxs-lookup"><span data-stu-id="d2ade-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2ade-104">方法</span><span class="sxs-lookup"><span data-stu-id="d2ade-104">Methods</span></span>  
  
|<span data-ttu-id="d2ade-105">方法</span><span class="sxs-lookup"><span data-stu-id="d2ade-105">Method</span></span>|<span data-ttu-id="d2ade-106">描述</span><span class="sxs-lookup"><span data-stu-id="d2ade-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2ade-107">ProvideLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="d2ade-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="d2ade-108">可讓偵錯工具提供可用來載入偵錯程式庫的模組的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d2ade-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2ade-109">需求</span><span class="sxs-lookup"><span data-stu-id="d2ade-109">Requirements</span></span>  
 <span data-ttu-id="d2ade-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2ade-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2ade-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2ade-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2ade-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2ade-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2ade-113">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2ade-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ade-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2ade-114">See also</span></span>
- [<span data-ttu-id="d2ade-115">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d2ade-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d2ade-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="d2ade-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
