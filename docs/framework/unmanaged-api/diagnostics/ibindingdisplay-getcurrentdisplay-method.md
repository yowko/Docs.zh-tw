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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 472e06c3a00762a7bb012fbcb525d8e0b3a9271a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162244"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="a2d7b-102">IBindingDisplay::GetCurrentDisplay 方法</span><span class="sxs-lookup"><span data-stu-id="a2d7b-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="a2d7b-103">傳回目前的繫結顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="a2d7b-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2d7b-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2d7b-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2d7b-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="a2d7b-106">[out，retval]包含繫結顯示資訊的 safearray 指標。</span><span class="sxs-lookup"><span data-stu-id="a2d7b-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d7b-107">備註</span><span class="sxs-lookup"><span data-stu-id="a2d7b-107">Remarks</span></span>  
 <span data-ttu-id="a2d7b-108">[Ibindingdisplay:: Initializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)方法必須有先前成功，且程式必須先停止偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a2d7b-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="a2d7b-109">呼叫端必須解除配置傳回`SAFEARRAY`使用的記憶體[SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)。</span><span class="sxs-lookup"><span data-stu-id="a2d7b-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d7b-110">需求</span><span class="sxs-lookup"><span data-stu-id="a2d7b-110">Requirements</span></span>  
 <span data-ttu-id="a2d7b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d7b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d7b-112">**標頭：** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="a2d7b-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="a2d7b-113">**LIBRARY:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="a2d7b-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="a2d7b-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d7b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d7b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2d7b-115">See also</span></span>

- [<span data-ttu-id="a2d7b-116">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="a2d7b-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="a2d7b-117">InitializeForProcess 方法</span><span class="sxs-lookup"><span data-stu-id="a2d7b-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
