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
ms.openlocfilehash: 7884d53630ca13a30d7b4efd55d46684a9dd7d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427638"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="256b5-102">ComCallUnmarshal Coclass</span><span class="sxs-lookup"><span data-stu-id="256b5-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="256b5-103">提供介面來管理的介面指標封送處理。</span><span class="sxs-lookup"><span data-stu-id="256b5-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="256b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="256b5-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="256b5-105">介面</span><span class="sxs-lookup"><span data-stu-id="256b5-105">Interfaces</span></span>  
  
|<span data-ttu-id="256b5-106">介面</span><span class="sxs-lookup"><span data-stu-id="256b5-106">Interface</span></span>|<span data-ttu-id="256b5-107">描述</span><span class="sxs-lookup"><span data-stu-id="256b5-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="256b5-108">提供方法來建立、 初始化及管理用戶端處理序中的 proxy。</span><span class="sxs-lookup"><span data-stu-id="256b5-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="256b5-109">需求</span><span class="sxs-lookup"><span data-stu-id="256b5-109">Requirements</span></span>  
 <span data-ttu-id="256b5-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="256b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="256b5-111">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="256b5-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="256b5-112">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="256b5-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="256b5-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="256b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="256b5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="256b5-114">See Also</span></span>  
 [<span data-ttu-id="256b5-115">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="256b5-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
