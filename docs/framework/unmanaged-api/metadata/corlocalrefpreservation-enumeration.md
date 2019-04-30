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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 845994b96445d8ec2a0e37affc5164b432894a91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045707"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="a3b83-102">CorLocalRefPreservation 列舉</span><span class="sxs-lookup"><span data-stu-id="a3b83-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="a3b83-103">包含代表本機參考處理方式的旗標值。</span><span class="sxs-lookup"><span data-stu-id="a3b83-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b83-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3b83-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="a3b83-105">成員</span><span class="sxs-lookup"><span data-stu-id="a3b83-105">Members</span></span>  
  
|<span data-ttu-id="a3b83-106">成員</span><span class="sxs-lookup"><span data-stu-id="a3b83-106">Member</span></span>|<span data-ttu-id="a3b83-107">描述</span><span class="sxs-lookup"><span data-stu-id="a3b83-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="a3b83-108">保留任何本機參考。</span><span class="sxs-lookup"><span data-stu-id="a3b83-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="a3b83-109">保留本機的型別參考。</span><span class="sxs-lookup"><span data-stu-id="a3b83-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="a3b83-110">保留本機成員的參考。</span><span class="sxs-lookup"><span data-stu-id="a3b83-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3b83-111">需求</span><span class="sxs-lookup"><span data-stu-id="a3b83-111">Requirements</span></span>  
 <span data-ttu-id="a3b83-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3b83-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3b83-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a3b83-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a3b83-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3b83-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b83-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3b83-115">See also</span></span>

- [<span data-ttu-id="a3b83-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="a3b83-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
