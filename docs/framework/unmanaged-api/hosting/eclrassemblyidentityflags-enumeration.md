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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18b7310b2d04b81330c68de59adf5f18ba9c8675
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769747"
---
# <a name="eclrassemblyidentityflags-enumeration"></a><span data-ttu-id="26245-102">ECLRAssemblyIdentityFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="26245-102">ECLRAssemblyIdentityFlags Enumeration</span></span>
<span data-ttu-id="26245-103">指示組件的身分識別的型別。</span><span class="sxs-lookup"><span data-stu-id="26245-103">Indicates the type of an assembly's identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26245-104">語法</span><span class="sxs-lookup"><span data-stu-id="26245-104">Syntax</span></span>  
  
```cpp  
typedef enum _CLRAssemblyIdentityFlags {  
    CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT = 0  
} ECLRAssemblyIdentityFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="26245-105">成員</span><span class="sxs-lookup"><span data-stu-id="26245-105">Members</span></span>  
  
|<span data-ttu-id="26245-106">成員</span><span class="sxs-lookup"><span data-stu-id="26245-106">Member</span></span>|<span data-ttu-id="26245-107">描述</span><span class="sxs-lookup"><span data-stu-id="26245-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT`|<span data-ttu-id="26245-108">正式的身分識別。</span><span class="sxs-lookup"><span data-stu-id="26245-108">The identity is canonicalized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26245-109">需求</span><span class="sxs-lookup"><span data-stu-id="26245-109">Requirements</span></span>  
 <span data-ttu-id="26245-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="26245-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26245-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26245-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26245-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26245-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26245-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26245-113">See also</span></span>

- [<span data-ttu-id="26245-114">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="26245-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
