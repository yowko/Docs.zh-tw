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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178447"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="eaea5-102">CorUnmanagedCallingConvention 列舉</span><span class="sxs-lookup"><span data-stu-id="eaea5-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="eaea5-103">指定 unmanaged 程式碼的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="eaea5-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaea5-104">語法</span><span class="sxs-lookup"><span data-stu-id="eaea5-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="eaea5-105">成員</span><span class="sxs-lookup"><span data-stu-id="eaea5-105">Members</span></span>  
  
|<span data-ttu-id="eaea5-106">成員</span><span class="sxs-lookup"><span data-stu-id="eaea5-106">Member</span></span>|<span data-ttu-id="eaea5-107">描述</span><span class="sxs-lookup"><span data-stu-id="eaea5-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="eaea5-108">C 語言的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="eaea5-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="eaea5-109">標準呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="eaea5-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="eaea5-110">"This"的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="eaea5-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="eaea5-111">「 快速 」 的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="eaea5-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="eaea5-112">未使用。</span><span class="sxs-lookup"><span data-stu-id="eaea5-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="eaea5-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="eaea5-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="eaea5-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="eaea5-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="eaea5-115">未使用。</span><span class="sxs-lookup"><span data-stu-id="eaea5-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaea5-116">備註</span><span class="sxs-lookup"><span data-stu-id="eaea5-116">Remarks</span></span>  
 <span data-ttu-id="eaea5-117">CLR 不支援.NET Framework 1.0 版中的 「 快速 」 的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="eaea5-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaea5-118">需求</span><span class="sxs-lookup"><span data-stu-id="eaea5-118">Requirements</span></span>  
 <span data-ttu-id="eaea5-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eaea5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaea5-120">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="eaea5-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eaea5-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaea5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaea5-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaea5-122">See also</span></span>

- [<span data-ttu-id="eaea5-123">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="eaea5-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
