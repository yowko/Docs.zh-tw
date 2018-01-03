---
title: "IBindingDisplay::GetCurrentDisplay 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.GetCurrentDisplay
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7013b07d0ebf2709d6c2b6f791960a8e7d35d678
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="5e32f-102">IBindingDisplay::GetCurrentDisplay 方法</span><span class="sxs-lookup"><span data-stu-id="5e32f-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="5e32f-103">傳回目前的繫結顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="5e32f-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e32f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e32f-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e32f-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e32f-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="5e32f-106">[out，retval]包含繫結顯示資訊的 safearray 指標。</span><span class="sxs-lookup"><span data-stu-id="5e32f-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e32f-107">備註</span><span class="sxs-lookup"><span data-stu-id="5e32f-107">Remarks</span></span>  
 <span data-ttu-id="5e32f-108">[Ibindingdisplay:: Initializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)方法必須有先前成功，而且該程式必須先停止偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5e32f-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="5e32f-109">呼叫端必須取消配置傳回`SAFEARRAY`記憶體使用[SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa)。</span><span class="sxs-lookup"><span data-stu-id="5e32f-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e32f-110">需求</span><span class="sxs-lookup"><span data-stu-id="5e32f-110">Requirements</span></span>  
 <span data-ttu-id="5e32f-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e32f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e32f-112">**標頭：** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="5e32f-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="5e32f-113">**程式庫：** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="5e32f-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="5e32f-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e32f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e32f-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e32f-115">See Also</span></span>  
 [<span data-ttu-id="5e32f-116">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="5e32f-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 [<span data-ttu-id="5e32f-117">InitializeForProcess 方法</span><span class="sxs-lookup"><span data-stu-id="5e32f-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
