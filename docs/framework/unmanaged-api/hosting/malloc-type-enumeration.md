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
ms.openlocfilehash: fe58a519d0feac0da49e7778247da1ef538f8b83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730028"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="a87ac-102">MALLOC_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="a87ac-102">MALLOC_TYPE Enumeration</span></span>

<span data-ttu-id="a87ac-103">包含值，這些值會指定所配置記憶體的特性。</span><span class="sxs-lookup"><span data-stu-id="a87ac-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="a87ac-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="a87ac-105">成員</span><span class="sxs-lookup"><span data-stu-id="a87ac-105">Members</span></span>  
  
|<span data-ttu-id="a87ac-106">member</span><span class="sxs-lookup"><span data-stu-id="a87ac-106">Member</span></span>|<span data-ttu-id="a87ac-107">描述</span><span class="sxs-lookup"><span data-stu-id="a87ac-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="a87ac-108">配置的記憶體可以包含可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a87ac-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="a87ac-109">配置的記憶體是安全線程。</span><span class="sxs-lookup"><span data-stu-id="a87ac-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="a87ac-110">也就是說，多個執行緒可以存取記憶體，而不需要進行任何同步處理。</span><span class="sxs-lookup"><span data-stu-id="a87ac-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="a87ac-111">如果未設定此旗標，則必須序列化物件上的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a87ac-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a87ac-112">需求</span><span class="sxs-lookup"><span data-stu-id="a87ac-112">Requirements</span></span>  

 <span data-ttu-id="a87ac-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a87ac-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a87ac-114">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a87ac-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a87ac-115">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a87ac-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a87ac-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a87ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87ac-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a87ac-117">See also</span></span>

- [<span data-ttu-id="a87ac-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="a87ac-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
