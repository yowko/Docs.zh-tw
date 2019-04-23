---
title: ComCallUnmarshal Coclass
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f17a88a90905006432ae8c5dc040277124c947b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166877"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="f78f8-102">ComCallUnmarshal Coclass</span><span class="sxs-lookup"><span data-stu-id="f78f8-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="f78f8-103">提供介面來管理的介面指標封送處理。</span><span class="sxs-lookup"><span data-stu-id="f78f8-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f78f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="f78f8-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="f78f8-105">介面</span><span class="sxs-lookup"><span data-stu-id="f78f8-105">Interfaces</span></span>  
  
|<span data-ttu-id="f78f8-106">介面</span><span class="sxs-lookup"><span data-stu-id="f78f8-106">Interface</span></span>|<span data-ttu-id="f78f8-107">描述</span><span class="sxs-lookup"><span data-stu-id="f78f8-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="f78f8-108">提供方法來建立、 初始化及管理用戶端處理序中的 proxy。</span><span class="sxs-lookup"><span data-stu-id="f78f8-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f78f8-109">需求</span><span class="sxs-lookup"><span data-stu-id="f78f8-109">Requirements</span></span>  
 <span data-ttu-id="f78f8-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f78f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f78f8-111">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="f78f8-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f78f8-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f78f8-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f78f8-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f78f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78f8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f78f8-114">See also</span></span>

- [<span data-ttu-id="f78f8-115">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="f78f8-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
