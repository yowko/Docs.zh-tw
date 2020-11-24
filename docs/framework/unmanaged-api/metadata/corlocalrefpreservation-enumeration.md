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
ms.openlocfilehash: 49b0298f4fa776c93f89ac380ce65568b493379b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677111"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="58117-102">CorLocalRefPreservation 列舉</span><span class="sxs-lookup"><span data-stu-id="58117-102">CorLocalRefPreservation Enumeration</span></span>

<span data-ttu-id="58117-103">包含代表本機參考處理方式的旗標值。</span><span class="sxs-lookup"><span data-stu-id="58117-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58117-104">語法</span><span class="sxs-lookup"><span data-stu-id="58117-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="58117-105">成員</span><span class="sxs-lookup"><span data-stu-id="58117-105">Members</span></span>  
  
|<span data-ttu-id="58117-106">member</span><span class="sxs-lookup"><span data-stu-id="58117-106">Member</span></span>|<span data-ttu-id="58117-107">描述</span><span class="sxs-lookup"><span data-stu-id="58117-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="58117-108">不保留本機參考。</span><span class="sxs-lookup"><span data-stu-id="58117-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="58117-109">保留區欄位型別參考。</span><span class="sxs-lookup"><span data-stu-id="58117-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="58117-110">保留本機成員參考。</span><span class="sxs-lookup"><span data-stu-id="58117-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58117-111">需求</span><span class="sxs-lookup"><span data-stu-id="58117-111">Requirements</span></span>  

 <span data-ttu-id="58117-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58117-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58117-113">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="58117-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="58117-114">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58117-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58117-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58117-115">See also</span></span>

- [<span data-ttu-id="58117-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="58117-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
