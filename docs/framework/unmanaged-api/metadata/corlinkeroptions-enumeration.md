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
ms.openlocfilehash: 188301d31b2fcfaf7b1c6139111e8f1296ccf7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677225"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="81a91-102">CorLinkerOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="81a91-102">CorLinkerOptions Enumeration</span></span>

<span data-ttu-id="81a91-103">指定旗標，以選取中繼資料連結器的選項。</span><span class="sxs-lookup"><span data-stu-id="81a91-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a91-104">語法</span><span class="sxs-lookup"><span data-stu-id="81a91-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="81a91-105">成員</span><span class="sxs-lookup"><span data-stu-id="81a91-105">Members</span></span>  
  
|<span data-ttu-id="81a91-106">member</span><span class="sxs-lookup"><span data-stu-id="81a91-106">Member</span></span>|<span data-ttu-id="81a91-107">描述</span><span class="sxs-lookup"><span data-stu-id="81a91-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="81a91-108">私用類型和全域函式並不會保留。</span><span class="sxs-lookup"><span data-stu-id="81a91-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="81a91-109">私用類型和全域函式會保留下來。</span><span class="sxs-lookup"><span data-stu-id="81a91-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81a91-110">需求</span><span class="sxs-lookup"><span data-stu-id="81a91-110">Requirements</span></span>  

 <span data-ttu-id="81a91-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81a91-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81a91-112">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="81a91-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="81a91-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81a91-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a91-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81a91-114">See also</span></span>

- [<span data-ttu-id="81a91-115">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="81a91-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
