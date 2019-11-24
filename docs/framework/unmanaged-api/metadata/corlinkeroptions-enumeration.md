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
ms.openlocfilehash: 086e17185df9caa823b44b51cf027f95d635c48d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450266"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="ebd3f-102">CorLinkerOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="ebd3f-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="ebd3f-103">指定旗標，以選取中繼資料連結器的選項。</span><span class="sxs-lookup"><span data-stu-id="ebd3f-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebd3f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="ebd3f-105">Members</span><span class="sxs-lookup"><span data-stu-id="ebd3f-105">Members</span></span>  
  
|<span data-ttu-id="ebd3f-106">成員</span><span class="sxs-lookup"><span data-stu-id="ebd3f-106">Member</span></span>|<span data-ttu-id="ebd3f-107">描述</span><span class="sxs-lookup"><span data-stu-id="ebd3f-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="ebd3f-108">The private types and global functions are not preserved.</span><span class="sxs-lookup"><span data-stu-id="ebd3f-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="ebd3f-109">The private types and global functions are preserved.</span><span class="sxs-lookup"><span data-stu-id="ebd3f-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ebd3f-110">需求</span><span class="sxs-lookup"><span data-stu-id="ebd3f-110">Requirements</span></span>  
 <span data-ttu-id="ebd3f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebd3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebd3f-112">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ebd3f-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ebd3f-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebd3f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd3f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ebd3f-114">See also</span></span>

- [<span data-ttu-id="ebd3f-115">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="ebd3f-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
