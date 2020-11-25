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
ms.openlocfilehash: 0f38314df766b74164bf5e98d9b2153d2dddbcc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721734"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="7ab32-102">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7ab32-102">IApartmentCallback Interface</span></span>

<span data-ttu-id="7ab32-103">提供在一個單元內進行回呼的方法。</span><span class="sxs-lookup"><span data-stu-id="7ab32-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="7ab32-104">若為共用相同執行緒存取需求的物件，則 *單元* 是進程內的邏輯容器。</span><span class="sxs-lookup"><span data-stu-id="7ab32-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ab32-105">方法</span><span class="sxs-lookup"><span data-stu-id="7ab32-105">Methods</span></span>  
  
|<span data-ttu-id="7ab32-106">方法</span><span class="sxs-lookup"><span data-stu-id="7ab32-106">Method</span></span>|<span data-ttu-id="7ab32-107">描述</span><span class="sxs-lookup"><span data-stu-id="7ab32-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ab32-108">DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="7ab32-108">DoCallback Method</span></span>](iapartmentcallback-docallback-method.md)|<span data-ttu-id="7ab32-109">在公寓內執行指定的函式。</span><span class="sxs-lookup"><span data-stu-id="7ab32-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ab32-110">需求</span><span class="sxs-lookup"><span data-stu-id="7ab32-110">Requirements</span></span>  

 <span data-ttu-id="7ab32-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab32-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab32-112">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7ab32-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ab32-113">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="7ab32-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ab32-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab32-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab32-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ab32-115">See also</span></span>

- [<span data-ttu-id="7ab32-116">裝載介面</span><span class="sxs-lookup"><span data-stu-id="7ab32-116">Hosting Interfaces</span></span>](hosting-interfaces.md)
