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
ms.openlocfilehash: dc0554ed89d21607978d059b26c4ad69e59a2d4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166630"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="2b1ff-102">CorLinkerOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="2b1ff-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="2b1ff-103">指定旗標，以選取中繼資料連結器的選項。</span><span class="sxs-lookup"><span data-stu-id="2b1ff-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b1ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b1ff-104">Syntax</span></span>  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="2b1ff-105">成員</span><span class="sxs-lookup"><span data-stu-id="2b1ff-105">Members</span></span>  
  
|<span data-ttu-id="2b1ff-106">成員</span><span class="sxs-lookup"><span data-stu-id="2b1ff-106">Member</span></span>|<span data-ttu-id="2b1ff-107">描述</span><span class="sxs-lookup"><span data-stu-id="2b1ff-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="2b1ff-108">不會保留私用類型和全域函式。</span><span class="sxs-lookup"><span data-stu-id="2b1ff-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="2b1ff-109">私用類型和全域函式會保留。</span><span class="sxs-lookup"><span data-stu-id="2b1ff-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b1ff-110">需求</span><span class="sxs-lookup"><span data-stu-id="2b1ff-110">Requirements</span></span>  
 <span data-ttu-id="2b1ff-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b1ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b1ff-112">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2b1ff-112">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="2b1ff-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="2b1ff-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b1ff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b1ff-114">See also</span></span>

- [<span data-ttu-id="2b1ff-115">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="2b1ff-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
