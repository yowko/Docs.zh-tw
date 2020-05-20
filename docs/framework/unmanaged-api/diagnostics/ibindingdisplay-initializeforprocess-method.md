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
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442146"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="5cb6b-102">IBindingDisplay::InitializeForProcess 方法</span><span class="sxs-lookup"><span data-stu-id="5cb6b-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="5cb6b-103">初始化[IBindingDisplay](ibindingdisplay-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="5cb6b-103">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cb6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5cb6b-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cb6b-105">參數</span><span class="sxs-lookup"><span data-stu-id="5cb6b-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="5cb6b-106">在處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="5cb6b-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cb6b-107">備註</span><span class="sxs-lookup"><span data-stu-id="5cb6b-107">Remarks</span></span>  
 <span data-ttu-id="5cb6b-108">偵錯工具會 `InitializeForProcess` 在建立時呼叫方法，以初始化系結顯示。</span><span class="sxs-lookup"><span data-stu-id="5cb6b-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="5cb6b-109">`InitializeForProcess`在呼叫上的任何其他方法之前，必須在建立期間呼叫 `IBindingDisplay` 。</span><span class="sxs-lookup"><span data-stu-id="5cb6b-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cb6b-110">需求</span><span class="sxs-lookup"><span data-stu-id="5cb6b-110">Requirements</span></span>  
 <span data-ttu-id="5cb6b-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5cb6b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cb6b-112">**標頭：** BindingDisplay。h</span><span class="sxs-lookup"><span data-stu-id="5cb6b-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="5cb6b-113">連結**庫：** BindingDisplay .idl</span><span class="sxs-lookup"><span data-stu-id="5cb6b-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="5cb6b-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cb6b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cb6b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cb6b-115">See also</span></span>

- [<span data-ttu-id="5cb6b-116">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="5cb6b-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
