---
title: "CorLocalRefPreservation 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLocalRefPreservation
api_location: mscoree.dll
api_type: COM
f1_keywords: CorLocalRefPreservation
helpviewer_keywords: CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eac01ce31e850eb02af84c0b84e58c1f0142242d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="804f9-102">CorLocalRefPreservation 列舉</span><span class="sxs-lookup"><span data-stu-id="804f9-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="804f9-103">包含代表本機參考處理方式的旗標值。</span><span class="sxs-lookup"><span data-stu-id="804f9-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="804f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="804f9-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="804f9-105">成員</span><span class="sxs-lookup"><span data-stu-id="804f9-105">Members</span></span>  
  
|<span data-ttu-id="804f9-106">成員</span><span class="sxs-lookup"><span data-stu-id="804f9-106">Member</span></span>|<span data-ttu-id="804f9-107">說明</span><span class="sxs-lookup"><span data-stu-id="804f9-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="804f9-108">保留本機參考。</span><span class="sxs-lookup"><span data-stu-id="804f9-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="804f9-109">保留本機類型參考。</span><span class="sxs-lookup"><span data-stu-id="804f9-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="804f9-110">保留本機成員的參考。</span><span class="sxs-lookup"><span data-stu-id="804f9-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="804f9-111">需求</span><span class="sxs-lookup"><span data-stu-id="804f9-111">Requirements</span></span>  
 <span data-ttu-id="804f9-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="804f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="804f9-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="804f9-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="804f9-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="804f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804f9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="804f9-115">See Also</span></span>  
 [<span data-ttu-id="804f9-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="804f9-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
