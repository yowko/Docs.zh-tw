---
title: "ICLRDebuggingLibraryProvider 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider
helpviewer_keywords: ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7320bf261f28fed85c44f2550df5ecd06421290
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="ea827-102">ICLRDebuggingLibraryProvider 介面</span><span class="sxs-lookup"><span data-stu-id="ea827-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="ea827-103">包含[ProvideLibrary 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)方法，就會取得程式庫提供者回呼介面，common language runtime 版本特定偵錯程式庫找到並載入需求。</span><span class="sxs-lookup"><span data-stu-id="ea827-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea827-104">方法</span><span class="sxs-lookup"><span data-stu-id="ea827-104">Methods</span></span>  
  
|<span data-ttu-id="ea827-105">方法</span><span class="sxs-lookup"><span data-stu-id="ea827-105">Method</span></span>|<span data-ttu-id="ea827-106">描述</span><span class="sxs-lookup"><span data-stu-id="ea827-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea827-107">ProvideLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="ea827-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="ea827-108">可讓偵錯工具，提供可以用來載入偵錯程式庫模組的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ea827-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea827-109">需求</span><span class="sxs-lookup"><span data-stu-id="ea827-109">Requirements</span></span>  
 <span data-ttu-id="ea827-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea827-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea827-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea827-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea827-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea827-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea827-113">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea827-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea827-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea827-114">See Also</span></span>  
 [<span data-ttu-id="ea827-115">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ea827-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ea827-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="ea827-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
