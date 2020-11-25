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
ms.openlocfilehash: cd17cbc808b7f8381ac320bb55999c6b0466c3d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723529"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="17cff-102">ICLRDebuggingLibraryProvider 介面</span><span class="sxs-lookup"><span data-stu-id="17cff-102">ICLRDebuggingLibraryProvider Interface</span></span>

<span data-ttu-id="17cff-103">包含 [ProvideLibrary 方法](iclrdebugginglibraryprovider-providelibrary-method.md) 方法，這個方法會取得程式庫提供者回呼介面，以便視需要尋找並載入 common language runtime 版本特定的偵錯工具庫。</span><span class="sxs-lookup"><span data-stu-id="17cff-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17cff-104">方法</span><span class="sxs-lookup"><span data-stu-id="17cff-104">Methods</span></span>  
  
|<span data-ttu-id="17cff-105">方法</span><span class="sxs-lookup"><span data-stu-id="17cff-105">Method</span></span>|<span data-ttu-id="17cff-106">描述</span><span class="sxs-lookup"><span data-stu-id="17cff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17cff-107">ProvideLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="17cff-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="17cff-108">允許偵錯工具提供模組的控制碼，可用來載入偵錯工具程式庫。</span><span class="sxs-lookup"><span data-stu-id="17cff-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17cff-109">需求</span><span class="sxs-lookup"><span data-stu-id="17cff-109">Requirements</span></span>  

 <span data-ttu-id="17cff-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17cff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17cff-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17cff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17cff-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17cff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17cff-113">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17cff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17cff-114">See also</span></span>

- [<span data-ttu-id="17cff-115">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="17cff-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="17cff-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="17cff-116">Debugging</span></span>](index.md)
