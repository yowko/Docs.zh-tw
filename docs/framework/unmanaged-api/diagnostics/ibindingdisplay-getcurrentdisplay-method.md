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
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442185"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="abb51-102">IBindingDisplay::GetCurrentDisplay 方法</span><span class="sxs-lookup"><span data-stu-id="abb51-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="abb51-103">傳回目前的系結顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="abb51-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb51-104">語法</span><span class="sxs-lookup"><span data-stu-id="abb51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abb51-105">參數</span><span class="sxs-lookup"><span data-stu-id="abb51-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="abb51-106">[out，retval]包含系結顯示資訊之 safearray 的指標。</span><span class="sxs-lookup"><span data-stu-id="abb51-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abb51-107">備註</span><span class="sxs-lookup"><span data-stu-id="abb51-107">Remarks</span></span>  
 <span data-ttu-id="abb51-108">[IBindingDisplay：： InitializeForProcess](ibindingdisplay-initializeforprocess-method.md)方法先前必須已成功，而且偵錯工具必須停止此程式。</span><span class="sxs-lookup"><span data-stu-id="abb51-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="abb51-109">呼叫端必須 `SAFEARRAY` 使用[SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)來解除配置傳回的記憶體。</span><span class="sxs-lookup"><span data-stu-id="abb51-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb51-110">需求</span><span class="sxs-lookup"><span data-stu-id="abb51-110">Requirements</span></span>  
 <span data-ttu-id="abb51-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abb51-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abb51-112">**標頭：** BindingDisplay。h</span><span class="sxs-lookup"><span data-stu-id="abb51-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="abb51-113">連結**庫：** BindingDisplay .idl</span><span class="sxs-lookup"><span data-stu-id="abb51-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="abb51-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abb51-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb51-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abb51-115">See also</span></span>

- [<span data-ttu-id="abb51-116">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="abb51-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="abb51-117">InitializeForProcess 方法</span><span class="sxs-lookup"><span data-stu-id="abb51-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
