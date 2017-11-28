---
title: "IApartmentCallback 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IApartmentCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: IApartmentCallback
helpviewer_keywords: IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d2f2ea73da2273ff6f0abb725ec3e3fb8ca79ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="d3257-102">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d3257-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="d3257-103">提供讓 apartment 內的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="d3257-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="d3257-104">*Apartment*是共用相同的執行緒存取需求的程序內的邏輯容器。</span><span class="sxs-lookup"><span data-stu-id="d3257-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3257-105">方法</span><span class="sxs-lookup"><span data-stu-id="d3257-105">Methods</span></span>  
  
|<span data-ttu-id="d3257-106">方法</span><span class="sxs-lookup"><span data-stu-id="d3257-106">Method</span></span>|<span data-ttu-id="d3257-107">說明</span><span class="sxs-lookup"><span data-stu-id="d3257-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3257-108">DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="d3257-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="d3257-109">執行指定的函式在 apartment 中。</span><span class="sxs-lookup"><span data-stu-id="d3257-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3257-110">需求</span><span class="sxs-lookup"><span data-stu-id="d3257-110">Requirements</span></span>  
 <span data-ttu-id="d3257-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3257-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3257-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3257-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3257-113">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d3257-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3257-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3257-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3257-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3257-115">See Also</span></span>  
 [<span data-ttu-id="d3257-116">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d3257-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
