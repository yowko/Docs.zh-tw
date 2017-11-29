---
title: "ICLRDebugging::CanUnloadNow 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging.CanUnloadNow Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b013231666ca6dfde5ab16e58023da1ae2a72941
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="b01f1-102">ICLRDebugging::CanUnloadNow 方法</span><span class="sxs-lookup"><span data-stu-id="b01f1-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="b01f1-103">決定是否由應用程式提供的文件庫[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面仍在使用或卸載。</span><span class="sxs-lookup"><span data-stu-id="b01f1-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b01f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="b01f1-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b01f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="b01f1-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="b01f1-106">[in]目標處理序模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="b01f1-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b01f1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b01f1-107">Return Value</span></span>  
 <span data-ttu-id="b01f1-108">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="b01f1-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b01f1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b01f1-109">HRESULT</span></span>|<span data-ttu-id="b01f1-110">描述</span><span class="sxs-lookup"><span data-stu-id="b01f1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b01f1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b01f1-111">S_OK</span></span>|<span data-ttu-id="b01f1-112">所參考的模組`hmodule`可以卸載。</span><span class="sxs-lookup"><span data-stu-id="b01f1-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="b01f1-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b01f1-113">S_FALSE</span></span>|<span data-ttu-id="b01f1-114">所參考的模組`hmodule`仍在使用中。</span><span class="sxs-lookup"><span data-stu-id="b01f1-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="b01f1-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="b01f1-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="b01f1-116">指定的模組不是 CLR 模組。</span><span class="sxs-lookup"><span data-stu-id="b01f1-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b01f1-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b01f1-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b01f1-118">備註</span><span class="sxs-lookup"><span data-stu-id="b01f1-118">Remarks</span></span>  
 <span data-ttu-id="b01f1-119">這個方法會檢查是否所有的執行個體`ICorDebug*`已發行的介面，任何執行緒目前的呼叫中[iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b01f1-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b01f1-120">需求</span><span class="sxs-lookup"><span data-stu-id="b01f1-120">Requirements</span></span>  
 <span data-ttu-id="b01f1-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b01f1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b01f1-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b01f1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b01f1-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b01f1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b01f1-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b01f1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b01f1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b01f1-125">See Also</span></span>  
 [<span data-ttu-id="b01f1-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b01f1-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b01f1-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="b01f1-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
