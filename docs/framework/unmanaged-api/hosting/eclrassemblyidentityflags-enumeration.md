---
title: ECLRAssemblyIdentityFlags 列舉
ms.date: 03/30/2017
api_name:
- ECLRAssemblyIdentityFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECLRAssemblyIdentityFlags
helpviewer_keywords:
- ECLRAssemblyIdentityFlags enumeration [.NET Framework hosting]
ms.assetid: d1e0b654-ccaf-4fa2-9aa3-8e007813c84d
topic_type:
- apiref
ms.openlocfilehash: c3fed9166d95c0ca71ac44f5447b95eee97af310
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726830"
---
# <a name="eclrassemblyidentityflags-enumeration"></a><span data-ttu-id="3804c-102">ECLRAssemblyIdentityFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="3804c-102">ECLRAssemblyIdentityFlags Enumeration</span></span>

<span data-ttu-id="3804c-103">表示元件的身分識別類型。</span><span class="sxs-lookup"><span data-stu-id="3804c-103">Indicates the type of an assembly's identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3804c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3804c-104">Syntax</span></span>  
  
```cpp  
typedef enum _CLRAssemblyIdentityFlags {  
    CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT = 0  
} ECLRAssemblyIdentityFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="3804c-105">成員</span><span class="sxs-lookup"><span data-stu-id="3804c-105">Members</span></span>  
  
|<span data-ttu-id="3804c-106">member</span><span class="sxs-lookup"><span data-stu-id="3804c-106">Member</span></span>|<span data-ttu-id="3804c-107">描述</span><span class="sxs-lookup"><span data-stu-id="3804c-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT`|<span data-ttu-id="3804c-108">身分識別是正式的。</span><span class="sxs-lookup"><span data-stu-id="3804c-108">The identity is canonicalized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3804c-109">需求</span><span class="sxs-lookup"><span data-stu-id="3804c-109">Requirements</span></span>  

 <span data-ttu-id="3804c-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3804c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3804c-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3804c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3804c-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3804c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3804c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3804c-113">See also</span></span>

- [<span data-ttu-id="3804c-114">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="3804c-114">Hosting Enumerations</span></span>](hosting-enumerations.md)
