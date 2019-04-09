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
ms.openlocfilehash: aa1e85751f90c34d40e88207af5c7eed2dd1bb82
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197860"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="0b409-102">IBindingDisplay::InitializeForProcess 方法</span><span class="sxs-lookup"><span data-stu-id="0b409-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="0b409-103">初始化[IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="0b409-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b409-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b409-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b409-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b409-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="0b409-106">[in]處理序識別碼中。</span><span class="sxs-lookup"><span data-stu-id="0b409-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b409-107">備註</span><span class="sxs-lookup"><span data-stu-id="0b409-107">Remarks</span></span>  
 <span data-ttu-id="0b409-108">偵錯工具呼叫`InitializeForProcess`來初始化繫結顯示建立時的方法。</span><span class="sxs-lookup"><span data-stu-id="0b409-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> `InitializeForProcess` <span data-ttu-id="0b409-109">必須在建立時，任何其他方法之前呼叫上`IBindingDisplay`呼叫。</span><span class="sxs-lookup"><span data-stu-id="0b409-109">must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b409-110">需求</span><span class="sxs-lookup"><span data-stu-id="0b409-110">Requirements</span></span>  
 <span data-ttu-id="0b409-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b409-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b409-112">**標頭：** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="0b409-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="0b409-113">**LIBRARY:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="0b409-113">**Library:** BindingDisplay.idl</span></span>  
  
 **<span data-ttu-id="0b409-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0b409-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0b409-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b409-115">See also</span></span>

- [<span data-ttu-id="0b409-116">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="0b409-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
