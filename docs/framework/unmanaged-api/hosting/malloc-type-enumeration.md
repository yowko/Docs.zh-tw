---
title: MALLOC_TYPE 列舉
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 695f69c8d9c3a295a705971743733339cf8aab13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765215"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="eba07-102">MALLOC_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="eba07-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="eba07-103">包含值，指定要配置的記憶體的特性。</span><span class="sxs-lookup"><span data-stu-id="eba07-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba07-104">語法</span><span class="sxs-lookup"><span data-stu-id="eba07-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="eba07-105">成員</span><span class="sxs-lookup"><span data-stu-id="eba07-105">Members</span></span>  
  
|<span data-ttu-id="eba07-106">成員</span><span class="sxs-lookup"><span data-stu-id="eba07-106">Member</span></span>|<span data-ttu-id="eba07-107">描述</span><span class="sxs-lookup"><span data-stu-id="eba07-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="eba07-108">配置的記憶體可以包含可執行檔。</span><span class="sxs-lookup"><span data-stu-id="eba07-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="eba07-109">配置的記憶體是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="eba07-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="eba07-110">也就是不需要任何同步處理多個執行緒可以存取的記憶體。</span><span class="sxs-lookup"><span data-stu-id="eba07-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="eba07-111">如果未設定此旗標，則必須序列化物件上的呼叫。</span><span class="sxs-lookup"><span data-stu-id="eba07-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eba07-112">需求</span><span class="sxs-lookup"><span data-stu-id="eba07-112">Requirements</span></span>  
 <span data-ttu-id="eba07-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eba07-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba07-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eba07-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eba07-115">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eba07-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eba07-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eba07-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba07-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eba07-117">See also</span></span>

- [<span data-ttu-id="eba07-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="eba07-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
