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
ms.openlocfilehash: 630fe4e79b369bfdefc19be72780f1893090895e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008452"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="93390-102">MALLOC_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="93390-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="93390-103">包含值，指定所配置記憶體的特性。</span><span class="sxs-lookup"><span data-stu-id="93390-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93390-104">語法</span><span class="sxs-lookup"><span data-stu-id="93390-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="93390-105">成員</span><span class="sxs-lookup"><span data-stu-id="93390-105">Members</span></span>  
  
|<span data-ttu-id="93390-106">成員</span><span class="sxs-lookup"><span data-stu-id="93390-106">Member</span></span>|<span data-ttu-id="93390-107">描述</span><span class="sxs-lookup"><span data-stu-id="93390-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="93390-108">配置的記憶體可以包含可執行檔。</span><span class="sxs-lookup"><span data-stu-id="93390-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="93390-109">配置的記憶體是安全線程。</span><span class="sxs-lookup"><span data-stu-id="93390-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="93390-110">也就是說，記憶體可由多個執行緒存取，而不需要任何同步處理。</span><span class="sxs-lookup"><span data-stu-id="93390-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="93390-111">如果未設定此旗標，則必須序列化物件上的呼叫。</span><span class="sxs-lookup"><span data-stu-id="93390-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93390-112">需求</span><span class="sxs-lookup"><span data-stu-id="93390-112">Requirements</span></span>  
 <span data-ttu-id="93390-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93390-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93390-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="93390-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93390-115">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="93390-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93390-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93390-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93390-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93390-117">See also</span></span>

- [<span data-ttu-id="93390-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="93390-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
