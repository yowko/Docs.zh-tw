---
title: IBindingDisplay::GetCurrentDisplay 方法
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 9294dbf1caddd4b607185de54efd2b4764e6ca35
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448500"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="03716-102">IBindingDisplay::GetCurrentDisplay 方法</span><span class="sxs-lookup"><span data-stu-id="03716-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="03716-103">傳回目前的系結顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="03716-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03716-104">語法</span><span class="sxs-lookup"><span data-stu-id="03716-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03716-105">參數</span><span class="sxs-lookup"><span data-stu-id="03716-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="03716-106">[out，retval]包含系結顯示資訊之 safearray 的指標。</span><span class="sxs-lookup"><span data-stu-id="03716-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03716-107">備註</span><span class="sxs-lookup"><span data-stu-id="03716-107">Remarks</span></span>  
 <span data-ttu-id="03716-108">[IBindingDisplay：： InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)方法先前必須已成功，而且偵錯工具必須停止此程式。</span><span class="sxs-lookup"><span data-stu-id="03716-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="03716-109">呼叫端必須使用[SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)，將傳回的 `SAFEARRAY` 記憶體解除配置。</span><span class="sxs-lookup"><span data-stu-id="03716-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03716-110">需求</span><span class="sxs-lookup"><span data-stu-id="03716-110">Requirements</span></span>  
 <span data-ttu-id="03716-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03716-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03716-112">**標頭：** BindingDisplay。h</span><span class="sxs-lookup"><span data-stu-id="03716-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="03716-113">連結**庫：** BindingDisplay .idl</span><span class="sxs-lookup"><span data-stu-id="03716-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="03716-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03716-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03716-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="03716-115">See also</span></span>

- [<span data-ttu-id="03716-116">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="03716-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="03716-117">InitializeForProcess 方法</span><span class="sxs-lookup"><span data-stu-id="03716-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
