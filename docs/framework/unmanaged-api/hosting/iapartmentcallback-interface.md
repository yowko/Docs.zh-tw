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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db933716cc0602ecda5da8a72726408ae4910179
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985502"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="d2e3f-102">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d2e3f-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="d2e3f-103">提供方法來進行回呼的 apartment 中。</span><span class="sxs-lookup"><span data-stu-id="d2e3f-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="d2e3f-104">*Apartment*是這些物件共用相同的執行緒存取需求的程序內的邏輯容器。</span><span class="sxs-lookup"><span data-stu-id="d2e3f-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2e3f-105">方法</span><span class="sxs-lookup"><span data-stu-id="d2e3f-105">Methods</span></span>  
  
|<span data-ttu-id="d2e3f-106">方法</span><span class="sxs-lookup"><span data-stu-id="d2e3f-106">Method</span></span>|<span data-ttu-id="d2e3f-107">描述</span><span class="sxs-lookup"><span data-stu-id="d2e3f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2e3f-108">DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="d2e3f-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="d2e3f-109">執行指定的函式中的 apartment。</span><span class="sxs-lookup"><span data-stu-id="d2e3f-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2e3f-110">需求</span><span class="sxs-lookup"><span data-stu-id="d2e3f-110">Requirements</span></span>  
 <span data-ttu-id="d2e3f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2e3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2e3f-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2e3f-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2e3f-113">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d2e3f-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2e3f-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2e3f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e3f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2e3f-115">See also</span></span>

- [<span data-ttu-id="d2e3f-116">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d2e3f-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
