---
title: IApartmentCallback::DoCallback 方法
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
ms.openlocfilehash: 1a56c3ebe4b1c528f9c6555bdfbf1270a438410d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617109"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="42419-102">IApartmentCallback::DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="42419-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="42419-103">在單元中執行指定的函式。</span><span class="sxs-lookup"><span data-stu-id="42419-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42419-104">語法</span><span class="sxs-lookup"><span data-stu-id="42419-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42419-105">參數</span><span class="sxs-lookup"><span data-stu-id="42419-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="42419-106">在要在單元內執行之函式的指標。</span><span class="sxs-lookup"><span data-stu-id="42419-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="42419-107">在函式引數的指標。</span><span class="sxs-lookup"><span data-stu-id="42419-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42419-108">需求</span><span class="sxs-lookup"><span data-stu-id="42419-108">Requirements</span></span>  
 <span data-ttu-id="42419-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42419-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42419-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="42419-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42419-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="42419-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42419-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42419-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42419-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42419-113">See also</span></span>

- [<span data-ttu-id="42419-114">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="42419-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
