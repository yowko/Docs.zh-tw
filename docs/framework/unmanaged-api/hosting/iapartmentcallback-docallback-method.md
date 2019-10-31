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
ms.openlocfilehash: 9bb257a3d84d5022b9ae13c89a34572485d3033b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126951"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="076f2-102">IApartmentCallback::DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="076f2-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="076f2-103">在單元中執行指定的函式。</span><span class="sxs-lookup"><span data-stu-id="076f2-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="076f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="076f2-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="076f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="076f2-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="076f2-106">在要在單元內執行之函式的指標。</span><span class="sxs-lookup"><span data-stu-id="076f2-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="076f2-107">在函式引數的指標。</span><span class="sxs-lookup"><span data-stu-id="076f2-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="076f2-108">需求</span><span class="sxs-lookup"><span data-stu-id="076f2-108">Requirements</span></span>  
 <span data-ttu-id="076f2-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="076f2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="076f2-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="076f2-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="076f2-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="076f2-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="076f2-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="076f2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="076f2-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="076f2-113">See also</span></span>

- [<span data-ttu-id="076f2-114">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="076f2-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
