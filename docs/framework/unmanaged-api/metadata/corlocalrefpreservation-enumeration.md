---
title: CorLocalRefPreservation 列舉
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
ms.openlocfilehash: 706ea37101f9f961e92d8cef2cf508c1dd0d56c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450237"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="c0f33-102">CorLocalRefPreservation 列舉</span><span class="sxs-lookup"><span data-stu-id="c0f33-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="c0f33-103">包含代表本機參考處理方式的旗標值。</span><span class="sxs-lookup"><span data-stu-id="c0f33-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0f33-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0f33-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="c0f33-105">Members</span><span class="sxs-lookup"><span data-stu-id="c0f33-105">Members</span></span>  
  
|<span data-ttu-id="c0f33-106">成員</span><span class="sxs-lookup"><span data-stu-id="c0f33-106">Member</span></span>|<span data-ttu-id="c0f33-107">描述</span><span class="sxs-lookup"><span data-stu-id="c0f33-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="c0f33-108">Preserve no local references.</span><span class="sxs-lookup"><span data-stu-id="c0f33-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="c0f33-109">Preserve local type references.</span><span class="sxs-lookup"><span data-stu-id="c0f33-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="c0f33-110">Preserve local member references.</span><span class="sxs-lookup"><span data-stu-id="c0f33-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0f33-111">需求</span><span class="sxs-lookup"><span data-stu-id="c0f33-111">Requirements</span></span>  
 <span data-ttu-id="c0f33-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f33-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0f33-113">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c0f33-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c0f33-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0f33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0f33-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f33-115">See also</span></span>

- [<span data-ttu-id="c0f33-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="c0f33-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
