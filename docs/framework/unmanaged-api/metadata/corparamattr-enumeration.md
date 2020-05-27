---
title: CorParamAttr 列舉
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: e8afcb972cab9757458c7032c3678d45c6418fac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007568"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="84832-102">CorParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="84832-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="84832-103">包含值，這些值描述方法參數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="84832-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84832-104">語法</span><span class="sxs-lookup"><span data-stu-id="84832-104">Syntax</span></span>  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="84832-105">成員</span><span class="sxs-lookup"><span data-stu-id="84832-105">Members</span></span>  
  
|<span data-ttu-id="84832-106">成員</span><span class="sxs-lookup"><span data-stu-id="84832-106">Member</span></span>|<span data-ttu-id="84832-107">描述</span><span class="sxs-lookup"><span data-stu-id="84832-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="84832-108">指定參數會傳遞至方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="84832-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="84832-109">指定從方法傳回傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="84832-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="84832-110">指定參數為選擇項。</span><span class="sxs-lookup"><span data-stu-id="84832-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="84832-111">保留供 common language runtime 內部使用。</span><span class="sxs-lookup"><span data-stu-id="84832-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="84832-112">指定此參數具有預設值。</span><span class="sxs-lookup"><span data-stu-id="84832-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="84832-113">指定參數具有封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="84832-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="84832-114">未使用的。</span><span class="sxs-lookup"><span data-stu-id="84832-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84832-115">需求</span><span class="sxs-lookup"><span data-stu-id="84832-115">Requirements</span></span>  
 <span data-ttu-id="84832-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84832-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84832-117">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="84832-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="84832-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84832-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84832-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84832-119">See also</span></span>

- [<span data-ttu-id="84832-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="84832-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
