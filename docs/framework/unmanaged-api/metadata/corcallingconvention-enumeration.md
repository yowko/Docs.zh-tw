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
ms.openlocfilehash: 310319e8fefe80017c58706e2beaee5eb1e78422
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007898"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="73fe5-102">CorCallingConvention 列舉</span><span class="sxs-lookup"><span data-stu-id="73fe5-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="73fe5-103">包含值，這些值描述在 Managed 程式碼中進行的呼叫慣例類型。</span><span class="sxs-lookup"><span data-stu-id="73fe5-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fe5-104">語法</span><span class="sxs-lookup"><span data-stu-id="73fe5-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="73fe5-105">成員</span><span class="sxs-lookup"><span data-stu-id="73fe5-105">Members</span></span>  
  
|<span data-ttu-id="73fe5-106">成員</span><span class="sxs-lookup"><span data-stu-id="73fe5-106">Member</span></span>|<span data-ttu-id="73fe5-107">描述</span><span class="sxs-lookup"><span data-stu-id="73fe5-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="73fe5-108">表示預設的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="73fe5-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="73fe5-109">表示方法會接受可變數目的參數。</span><span class="sxs-lookup"><span data-stu-id="73fe5-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="73fe5-110">表示呼叫的是欄位。</span><span class="sxs-lookup"><span data-stu-id="73fe5-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="73fe5-111">表示呼叫至區域方法。</span><span class="sxs-lookup"><span data-stu-id="73fe5-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="73fe5-112">表示呼叫的是屬性。</span><span class="sxs-lookup"><span data-stu-id="73fe5-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="73fe5-113">表示此呼叫未受管理。</span><span class="sxs-lookup"><span data-stu-id="73fe5-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="73fe5-114">表示泛型方法具現化。</span><span class="sxs-lookup"><span data-stu-id="73fe5-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="73fe5-115">表示對採用可變數目參數的方法進行64位 PInvoke 呼叫。</span><span class="sxs-lookup"><span data-stu-id="73fe5-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="73fe5-116">描述不正確4位值。</span><span class="sxs-lookup"><span data-stu-id="73fe5-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="73fe5-117">表示呼叫慣例是由下面四個位所描述。</span><span class="sxs-lookup"><span data-stu-id="73fe5-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="73fe5-118">表示上位會描述 `this` 參數。</span><span class="sxs-lookup"><span data-stu-id="73fe5-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="73fe5-119">表示在簽章 `this` 中明確描述參數。</span><span class="sxs-lookup"><span data-stu-id="73fe5-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="73fe5-120">表示具有明確數目之類型引數的泛型方法簽章。</span><span class="sxs-lookup"><span data-stu-id="73fe5-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="73fe5-121">這會優先于一般參數計數。</span><span class="sxs-lookup"><span data-stu-id="73fe5-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73fe5-122">需求</span><span class="sxs-lookup"><span data-stu-id="73fe5-122">Requirements</span></span>  
 <span data-ttu-id="73fe5-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73fe5-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73fe5-124">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="73fe5-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="73fe5-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73fe5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fe5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73fe5-126">See also</span></span>

- [<span data-ttu-id="73fe5-127">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="73fe5-127">Metadata Enumerations</span></span>](metadata-enumerations.md)
