---
title: CorCallingConvention 列舉
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: c9b20500a4a9e4649a938e00e3b059d1395da1d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718926"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="1f407-102">CorCallingConvention 列舉</span><span class="sxs-lookup"><span data-stu-id="1f407-102">CorCallingConvention Enumeration</span></span>

<span data-ttu-id="1f407-103">包含值，這些值描述在 Managed 程式碼中進行的呼叫慣例類型。</span><span class="sxs-lookup"><span data-stu-id="1f407-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f407-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f407-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="1f407-105">成員</span><span class="sxs-lookup"><span data-stu-id="1f407-105">Members</span></span>  
  
|<span data-ttu-id="1f407-106">member</span><span class="sxs-lookup"><span data-stu-id="1f407-106">Member</span></span>|<span data-ttu-id="1f407-107">描述</span><span class="sxs-lookup"><span data-stu-id="1f407-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="1f407-108">表示預設呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="1f407-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="1f407-109">指出方法接受參數數目的參數。</span><span class="sxs-lookup"><span data-stu-id="1f407-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="1f407-110">指出對欄位的呼叫。</span><span class="sxs-lookup"><span data-stu-id="1f407-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="1f407-111">指出呼叫的是本機方法。</span><span class="sxs-lookup"><span data-stu-id="1f407-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="1f407-112">指出對屬性的呼叫。</span><span class="sxs-lookup"><span data-stu-id="1f407-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="1f407-113">表示呼叫未受管理。</span><span class="sxs-lookup"><span data-stu-id="1f407-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="1f407-114">指出泛型方法具現化。</span><span class="sxs-lookup"><span data-stu-id="1f407-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="1f407-115">指出採用可變數參數數目之方法的64位 PInvoke 呼叫。</span><span class="sxs-lookup"><span data-stu-id="1f407-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="1f407-116">描述不正確4位值。</span><span class="sxs-lookup"><span data-stu-id="1f407-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="1f407-117">指出呼叫慣例是由底部四個位所描述。</span><span class="sxs-lookup"><span data-stu-id="1f407-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="1f407-118">指出 top 位描述 `this` 參數。</span><span class="sxs-lookup"><span data-stu-id="1f407-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="1f407-119">指出簽章 `this` 中已明確描述參數。</span><span class="sxs-lookup"><span data-stu-id="1f407-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="1f407-120">表示具有明確數目之類型引數的泛型方法簽章。</span><span class="sxs-lookup"><span data-stu-id="1f407-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="1f407-121">這是在一般的參數計數之前。</span><span class="sxs-lookup"><span data-stu-id="1f407-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f407-122">需求</span><span class="sxs-lookup"><span data-stu-id="1f407-122">Requirements</span></span>  

 <span data-ttu-id="1f407-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f407-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f407-124">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="1f407-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1f407-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f407-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f407-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f407-126">See also</span></span>

- [<span data-ttu-id="1f407-127">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="1f407-127">Metadata Enumerations</span></span>](metadata-enumerations.md)
