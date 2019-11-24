---
title: CorUnmanagedCallingConvention 列舉
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: 58d30e71929d314ee36adb9f83270858ff8a161b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442445"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="6486e-102">CorUnmanagedCallingConvention 列舉</span><span class="sxs-lookup"><span data-stu-id="6486e-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="6486e-103">Specifies the calling conventions for unmanaged code.</span><span class="sxs-lookup"><span data-stu-id="6486e-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6486e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6486e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="6486e-105">Members</span><span class="sxs-lookup"><span data-stu-id="6486e-105">Members</span></span>  
  
|<span data-ttu-id="6486e-106">成員</span><span class="sxs-lookup"><span data-stu-id="6486e-106">Member</span></span>|<span data-ttu-id="6486e-107">描述</span><span class="sxs-lookup"><span data-stu-id="6486e-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="6486e-108">The C language calling convention.</span><span class="sxs-lookup"><span data-stu-id="6486e-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="6486e-109">The standard calling convention.</span><span class="sxs-lookup"><span data-stu-id="6486e-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="6486e-110">The "this" calling convention.</span><span class="sxs-lookup"><span data-stu-id="6486e-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="6486e-111">The "fast" calling convention.</span><span class="sxs-lookup"><span data-stu-id="6486e-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="6486e-112">未使用。</span><span class="sxs-lookup"><span data-stu-id="6486e-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="6486e-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="6486e-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="6486e-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="6486e-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="6486e-115">未使用。</span><span class="sxs-lookup"><span data-stu-id="6486e-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6486e-116">備註</span><span class="sxs-lookup"><span data-stu-id="6486e-116">Remarks</span></span>  
 <span data-ttu-id="6486e-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span><span class="sxs-lookup"><span data-stu-id="6486e-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6486e-118">需求</span><span class="sxs-lookup"><span data-stu-id="6486e-118">Requirements</span></span>  
 <span data-ttu-id="6486e-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6486e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6486e-120">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6486e-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6486e-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6486e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6486e-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="6486e-122">See also</span></span>

- [<span data-ttu-id="6486e-123">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="6486e-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
