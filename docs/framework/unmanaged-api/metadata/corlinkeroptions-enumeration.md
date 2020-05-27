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
ms.openlocfilehash: fe5ffbab93df7168015e2a31d6e32ec45dce0960
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007685"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="9ae90-102">CorLinkerOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="9ae90-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="9ae90-103">指定旗標，以選取中繼資料連結器的選項。</span><span class="sxs-lookup"><span data-stu-id="9ae90-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ae90-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ae90-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="9ae90-105">成員</span><span class="sxs-lookup"><span data-stu-id="9ae90-105">Members</span></span>  
  
|<span data-ttu-id="9ae90-106">成員</span><span class="sxs-lookup"><span data-stu-id="9ae90-106">Member</span></span>|<span data-ttu-id="9ae90-107">描述</span><span class="sxs-lookup"><span data-stu-id="9ae90-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="9ae90-108">不會保留私用類型和全域函式。</span><span class="sxs-lookup"><span data-stu-id="9ae90-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="9ae90-109">會保留私用類型和全域函式。</span><span class="sxs-lookup"><span data-stu-id="9ae90-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ae90-110">需求</span><span class="sxs-lookup"><span data-stu-id="9ae90-110">Requirements</span></span>  
 <span data-ttu-id="9ae90-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae90-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ae90-112">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="9ae90-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9ae90-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ae90-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae90-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae90-114">See also</span></span>

- [<span data-ttu-id="9ae90-115">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="9ae90-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
