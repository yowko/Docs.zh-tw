---
title: "IBindingDisplay::InitializeForProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56f55788fcaf08507f413a03c5364ce3bcdbbf3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="d88b4-102">IBindingDisplay::InitializeForProcess 方法</span><span class="sxs-lookup"><span data-stu-id="d88b4-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="d88b4-103">初始化[IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="d88b4-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d88b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="d88b4-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d88b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="d88b4-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="d88b4-106">[in]處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="d88b4-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d88b4-107">備註</span><span class="sxs-lookup"><span data-stu-id="d88b4-107">Remarks</span></span>  
 <span data-ttu-id="d88b4-108">偵錯工具呼叫`InitializeForProcess`方法來初始化繫結顯示建立時間。</span><span class="sxs-lookup"><span data-stu-id="d88b4-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="d88b4-109">`InitializeForProcess`必須在建立時，任何其他方法之前呼叫上`IBindingDisplay`呼叫。</span><span class="sxs-lookup"><span data-stu-id="d88b4-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d88b4-110">需求</span><span class="sxs-lookup"><span data-stu-id="d88b4-110">Requirements</span></span>  
 <span data-ttu-id="d88b4-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d88b4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d88b4-112">**標頭：** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="d88b4-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="d88b4-113">**程式庫：** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="d88b4-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="d88b4-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d88b4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88b4-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d88b4-115">See Also</span></span>  
 [<span data-ttu-id="d88b4-116">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="d88b4-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
