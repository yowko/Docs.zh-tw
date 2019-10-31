---
title: IApartmentCallback 介面
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
ms.openlocfilehash: 4424509c16dd1d9f83db117ae7343fa03995297e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126903"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="ca50c-102">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ca50c-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="ca50c-103">提供在單元內進行回呼的方法。</span><span class="sxs-lookup"><span data-stu-id="ca50c-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="ca50c-104">在共用相同執行緒存取需求之物件的進程內，「*公寓*」是一個邏輯容器。</span><span class="sxs-lookup"><span data-stu-id="ca50c-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca50c-105">方法</span><span class="sxs-lookup"><span data-stu-id="ca50c-105">Methods</span></span>  
  
|<span data-ttu-id="ca50c-106">方法</span><span class="sxs-lookup"><span data-stu-id="ca50c-106">Method</span></span>|<span data-ttu-id="ca50c-107">描述</span><span class="sxs-lookup"><span data-stu-id="ca50c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca50c-108">DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="ca50c-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="ca50c-109">在單元中執行指定的函式。</span><span class="sxs-lookup"><span data-stu-id="ca50c-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca50c-110">需求</span><span class="sxs-lookup"><span data-stu-id="ca50c-110">Requirements</span></span>  
 <span data-ttu-id="ca50c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca50c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca50c-112">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ca50c-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca50c-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ca50c-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca50c-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca50c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca50c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca50c-115">See also</span></span>

- [<span data-ttu-id="ca50c-116">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ca50c-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
