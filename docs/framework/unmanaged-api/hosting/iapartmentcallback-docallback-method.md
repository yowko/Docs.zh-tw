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
ms.openlocfilehash: e3031bf123ff9107b4cebc0723f1be0d423bdaec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721747"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="814b9-102">IApartmentCallback::DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="814b9-102">IApartmentCallback::DoCallback Method</span></span>

<span data-ttu-id="814b9-103">在公寓內執行指定的函式。</span><span class="sxs-lookup"><span data-stu-id="814b9-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="814b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="814b9-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="814b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="814b9-105">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="814b9-106">在要在單元內執行之函式的指標。</span><span class="sxs-lookup"><span data-stu-id="814b9-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="814b9-107">在函數之引數的指標。</span><span class="sxs-lookup"><span data-stu-id="814b9-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="814b9-108">需求</span><span class="sxs-lookup"><span data-stu-id="814b9-108">Requirements</span></span>  

 <span data-ttu-id="814b9-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="814b9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="814b9-110">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="814b9-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="814b9-111">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="814b9-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="814b9-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="814b9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814b9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="814b9-113">See also</span></span>

- [<span data-ttu-id="814b9-114">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="814b9-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
