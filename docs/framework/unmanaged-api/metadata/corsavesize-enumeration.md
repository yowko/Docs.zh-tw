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
ms.openlocfilehash: 13a4364244f7d0076d77d14c3e3ef161e3872bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176132"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="f23d6-102">CorSaveSize 列舉</span><span class="sxs-lookup"><span data-stu-id="f23d6-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="f23d6-103">包含值，這些值表示在查詢儲存作業的大小時所需的精確度等級。</span><span class="sxs-lookup"><span data-stu-id="f23d6-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f23d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="f23d6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="f23d6-105">成員</span><span class="sxs-lookup"><span data-stu-id="f23d6-105">Members</span></span>  
  
|<span data-ttu-id="f23d6-106">member</span><span class="sxs-lookup"><span data-stu-id="f23d6-106">Member</span></span>|<span data-ttu-id="f23d6-107">描述</span><span class="sxs-lookup"><span data-stu-id="f23d6-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="f23d6-108">指定傳回值應精確。</span><span class="sxs-lookup"><span data-stu-id="f23d6-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="f23d6-109">指定應估計傳回值。</span><span class="sxs-lookup"><span data-stu-id="f23d6-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="f23d6-110">指定應刪除可丟棄的類型。</span><span class="sxs-lookup"><span data-stu-id="f23d6-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f23d6-111">需求</span><span class="sxs-lookup"><span data-stu-id="f23d6-111">Requirements</span></span>  
 <span data-ttu-id="f23d6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f23d6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f23d6-113">**標題：** 科爾赫德</span><span class="sxs-lookup"><span data-stu-id="f23d6-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f23d6-114">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f23d6-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f23d6-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f23d6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23d6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f23d6-116">See also</span></span>

- [<span data-ttu-id="f23d6-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f23d6-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
