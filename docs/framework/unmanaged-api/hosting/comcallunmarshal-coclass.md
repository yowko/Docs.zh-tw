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
ms.openlocfilehash: 90bcf4f37631e0246e58cc14bfcd331d981e4713
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731718"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="617de-102">ComCallUnmarshal Coclass</span><span class="sxs-lookup"><span data-stu-id="617de-102">ComCallUnmarshal Coclass</span></span>

<span data-ttu-id="617de-103">提供介面來管理介面指標的封送處理。</span><span class="sxs-lookup"><span data-stu-id="617de-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="617de-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="617de-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="617de-105">介面</span><span class="sxs-lookup"><span data-stu-id="617de-105">Interfaces</span></span>  
  
|<span data-ttu-id="617de-106">介面</span><span class="sxs-lookup"><span data-stu-id="617de-106">Interface</span></span>|<span data-ttu-id="617de-107">描述</span><span class="sxs-lookup"><span data-stu-id="617de-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="617de-108">提供在用戶端進程中建立、初始化和管理 proxy 的方法。</span><span class="sxs-lookup"><span data-stu-id="617de-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="617de-109">需求</span><span class="sxs-lookup"><span data-stu-id="617de-109">Requirements</span></span>  

 <span data-ttu-id="617de-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="617de-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="617de-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="617de-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="617de-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="617de-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="617de-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="617de-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617de-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="617de-114">See also</span></span>

- [<span data-ttu-id="617de-115">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="617de-115">Hosting Coclasses</span></span>](hosting-coclasses.md)
