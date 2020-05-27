---
title: CorSaveSize 列舉
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 22a7f87a5803dc185052a5ce7ed427eff9f8fb18
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009180"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="4e8d8-102">CorSaveSize 列舉</span><span class="sxs-lookup"><span data-stu-id="4e8d8-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="4e8d8-103">包含值，這些值表示在查詢儲存作業的大小時所需的精確度等級。</span><span class="sxs-lookup"><span data-stu-id="4e8d8-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e8d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e8d8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="4e8d8-105">成員</span><span class="sxs-lookup"><span data-stu-id="4e8d8-105">Members</span></span>  
  
|<span data-ttu-id="4e8d8-106">成員</span><span class="sxs-lookup"><span data-stu-id="4e8d8-106">Member</span></span>|<span data-ttu-id="4e8d8-107">描述</span><span class="sxs-lookup"><span data-stu-id="4e8d8-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="4e8d8-108">指定傳回值應該是精確的。</span><span class="sxs-lookup"><span data-stu-id="4e8d8-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="4e8d8-109">指定應估計傳回值。</span><span class="sxs-lookup"><span data-stu-id="4e8d8-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="4e8d8-110">指定應該移除可捨棄類型。</span><span class="sxs-lookup"><span data-stu-id="4e8d8-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e8d8-111">需求</span><span class="sxs-lookup"><span data-stu-id="4e8d8-111">Requirements</span></span>  
 <span data-ttu-id="4e8d8-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e8d8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e8d8-113">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="4e8d8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4e8d8-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4e8d8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e8d8-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e8d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e8d8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e8d8-116">See also</span></span>

- [<span data-ttu-id="4e8d8-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="4e8d8-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
