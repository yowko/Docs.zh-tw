---
title: IBindingDisplay::InitializeForProcess 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aabad159b521207fed976636ae8b9e338f09ac42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466176"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="dafc8-102">IBindingDisplay::InitializeForProcess 方法</span><span class="sxs-lookup"><span data-stu-id="dafc8-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="dafc8-103">初始化[IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="dafc8-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dafc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="dafc8-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dafc8-105">參數</span><span class="sxs-lookup"><span data-stu-id="dafc8-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="dafc8-106">[in]處理序識別碼中。</span><span class="sxs-lookup"><span data-stu-id="dafc8-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dafc8-107">備註</span><span class="sxs-lookup"><span data-stu-id="dafc8-107">Remarks</span></span>  
 <span data-ttu-id="dafc8-108">偵錯工具呼叫`InitializeForProcess`來初始化繫結顯示建立時的方法。</span><span class="sxs-lookup"><span data-stu-id="dafc8-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="dafc8-109">`InitializeForProcess` 必須在建立時，任何其他方法之前呼叫上`IBindingDisplay`呼叫。</span><span class="sxs-lookup"><span data-stu-id="dafc8-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dafc8-110">需求</span><span class="sxs-lookup"><span data-stu-id="dafc8-110">Requirements</span></span>  
 <span data-ttu-id="dafc8-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dafc8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dafc8-112">**標頭：** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="dafc8-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="dafc8-113">**程式庫：** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="dafc8-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="dafc8-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dafc8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dafc8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dafc8-115">See also</span></span>
- [<span data-ttu-id="dafc8-116">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="dafc8-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
