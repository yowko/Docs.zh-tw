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
ms.openlocfilehash: 77c2011ce677d1bd2823d47740782f48151b408a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860276"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="6d8a3-102">ICLRDebuggingLibraryProvider 介面</span><span class="sxs-lookup"><span data-stu-id="6d8a3-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="6d8a3-103">包含[ProvideLibrary 方法](iclrdebugginglibraryprovider-providelibrary-method.md)方法，它會取得程式庫提供者回呼介面，允許視需要尋找和載入 common language runtime 版本特定的偵錯工具程式庫。</span><span class="sxs-lookup"><span data-stu-id="6d8a3-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d8a3-104">方法</span><span class="sxs-lookup"><span data-stu-id="6d8a3-104">Methods</span></span>  
  
|<span data-ttu-id="6d8a3-105">方法</span><span class="sxs-lookup"><span data-stu-id="6d8a3-105">Method</span></span>|<span data-ttu-id="6d8a3-106">描述</span><span class="sxs-lookup"><span data-stu-id="6d8a3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d8a3-107">ProvideLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="6d8a3-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="6d8a3-108">可讓偵錯工具提供模組的控制碼，以用來載入偵錯工具程式庫。</span><span class="sxs-lookup"><span data-stu-id="6d8a3-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d8a3-109">需求</span><span class="sxs-lookup"><span data-stu-id="6d8a3-109">Requirements</span></span>  
 <span data-ttu-id="6d8a3-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d8a3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d8a3-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d8a3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d8a3-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d8a3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d8a3-113">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d8a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d8a3-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6d8a3-114">See also</span></span>

- [<span data-ttu-id="6d8a3-115">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6d8a3-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6d8a3-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="6d8a3-116">Debugging</span></span>](index.md)
