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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff308a81282a1cc14c35583daf9cbb057149e556
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178447"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="209dd-102">CorUnmanagedCallingConvention 列舉</span><span class="sxs-lookup"><span data-stu-id="209dd-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="209dd-103">指定 unmanaged 程式碼的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="209dd-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="209dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="209dd-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="209dd-105">成員</span><span class="sxs-lookup"><span data-stu-id="209dd-105">Members</span></span>  
  
|<span data-ttu-id="209dd-106">成員</span><span class="sxs-lookup"><span data-stu-id="209dd-106">Member</span></span>|<span data-ttu-id="209dd-107">描述</span><span class="sxs-lookup"><span data-stu-id="209dd-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="209dd-108">C 語言的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="209dd-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="209dd-109">標準呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="209dd-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="209dd-110">"This"的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="209dd-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="209dd-111">「 快速 」 的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="209dd-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="209dd-112">未使用。</span><span class="sxs-lookup"><span data-stu-id="209dd-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="209dd-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="209dd-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="209dd-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="209dd-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="209dd-115">未使用。</span><span class="sxs-lookup"><span data-stu-id="209dd-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="209dd-116">備註</span><span class="sxs-lookup"><span data-stu-id="209dd-116">Remarks</span></span>  
 <span data-ttu-id="209dd-117">CLR 不支援.NET Framework 1.0 版中的 「 快速 」 的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="209dd-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="209dd-118">需求</span><span class="sxs-lookup"><span data-stu-id="209dd-118">Requirements</span></span>  
 <span data-ttu-id="209dd-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="209dd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="209dd-120">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="209dd-120">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="209dd-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="209dd-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="209dd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="209dd-122">See also</span></span>

- [<span data-ttu-id="209dd-123">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="209dd-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
