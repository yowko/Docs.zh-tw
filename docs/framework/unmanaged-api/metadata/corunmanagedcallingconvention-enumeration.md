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
ms.openlocfilehash: b4c521489f38360d45c2cf8ff3780e057299f0b4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008946"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="a4c44-102">CorUnmanagedCallingConvention 列舉</span><span class="sxs-lookup"><span data-stu-id="a4c44-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="a4c44-103">指定非受控碼的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="a4c44-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c44-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4c44-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a4c44-105">成員</span><span class="sxs-lookup"><span data-stu-id="a4c44-105">Members</span></span>  
  
|<span data-ttu-id="a4c44-106">成員</span><span class="sxs-lookup"><span data-stu-id="a4c44-106">Member</span></span>|<span data-ttu-id="a4c44-107">描述</span><span class="sxs-lookup"><span data-stu-id="a4c44-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="a4c44-108">C 語言呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="a4c44-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="a4c44-109">標準呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="a4c44-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="a4c44-110">「這個」呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="a4c44-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="a4c44-111">「快速」呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="a4c44-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="a4c44-112">未使用。</span><span class="sxs-lookup"><span data-stu-id="a4c44-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="a4c44-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="a4c44-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="a4c44-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="a4c44-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="a4c44-115">未使用。</span><span class="sxs-lookup"><span data-stu-id="a4c44-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4c44-116">備註</span><span class="sxs-lookup"><span data-stu-id="a4c44-116">Remarks</span></span>  
 <span data-ttu-id="a4c44-117">CLR 不支援 .NET Framework 版本1.0 中的「快速」呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="a4c44-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c44-118">需求</span><span class="sxs-lookup"><span data-stu-id="a4c44-118">Requirements</span></span>  
 <span data-ttu-id="a4c44-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4c44-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c44-120">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="a4c44-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a4c44-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c44-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c44-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4c44-122">See also</span></span>

- [<span data-ttu-id="a4c44-123">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="a4c44-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
