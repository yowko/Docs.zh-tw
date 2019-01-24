---
title: CorLinkerOptions 列舉
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a072e124343641c9f75fb9f924a6409efc8e1d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719933"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="72991-102">CorLinkerOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="72991-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="72991-103">指定旗標，以選取中繼資料連結器的選項。</span><span class="sxs-lookup"><span data-stu-id="72991-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72991-104">語法</span><span class="sxs-lookup"><span data-stu-id="72991-104">Syntax</span></span>  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="72991-105">成員</span><span class="sxs-lookup"><span data-stu-id="72991-105">Members</span></span>  
  
|<span data-ttu-id="72991-106">成員</span><span class="sxs-lookup"><span data-stu-id="72991-106">Member</span></span>|<span data-ttu-id="72991-107">描述</span><span class="sxs-lookup"><span data-stu-id="72991-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="72991-108">不會保留私用類型和全域函式。</span><span class="sxs-lookup"><span data-stu-id="72991-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="72991-109">私用類型和全域函式會保留。</span><span class="sxs-lookup"><span data-stu-id="72991-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72991-110">需求</span><span class="sxs-lookup"><span data-stu-id="72991-110">Requirements</span></span>  
 <span data-ttu-id="72991-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72991-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72991-112">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="72991-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="72991-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72991-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72991-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72991-114">See also</span></span>
- [<span data-ttu-id="72991-115">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="72991-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
