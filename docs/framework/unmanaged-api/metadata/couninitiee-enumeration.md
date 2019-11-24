---
title: COUNINITIEE 列舉
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: 57054bdb7e3b991bc81985c02ec72a4110f31d60
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436443"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="70bc4-102">COUNINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="70bc4-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="70bc4-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="70bc4-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70bc4-104">語法</span><span class="sxs-lookup"><span data-stu-id="70bc4-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="70bc4-105">Members</span><span class="sxs-lookup"><span data-stu-id="70bc4-105">Members</span></span>  
  
|<span data-ttu-id="70bc4-106">成員</span><span class="sxs-lookup"><span data-stu-id="70bc4-106">Member</span></span>|<span data-ttu-id="70bc4-107">描述</span><span class="sxs-lookup"><span data-stu-id="70bc4-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="70bc4-108">Indicates default uninitialization mode.</span><span class="sxs-lookup"><span data-stu-id="70bc4-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="70bc4-109">Indicates uninitialization mode for unloading an assembly.</span><span class="sxs-lookup"><span data-stu-id="70bc4-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70bc4-110">需求</span><span class="sxs-lookup"><span data-stu-id="70bc4-110">Requirements</span></span>  
 <span data-ttu-id="70bc4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70bc4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70bc4-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70bc4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70bc4-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70bc4-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70bc4-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70bc4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bc4-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="70bc4-115">See also</span></span>

- [<span data-ttu-id="70bc4-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="70bc4-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
