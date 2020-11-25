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
ms.openlocfilehash: 6f5d022a96fa021cb28dbbb67d0b53e08f77498c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729277"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="72cf0-102">CorParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="72cf0-102">CorParamAttr Enumeration</span></span>

<span data-ttu-id="72cf0-103">包含值，這些值描述方法參數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="72cf0-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72cf0-104">語法</span><span class="sxs-lookup"><span data-stu-id="72cf0-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="72cf0-105">成員</span><span class="sxs-lookup"><span data-stu-id="72cf0-105">Members</span></span>  
  
|<span data-ttu-id="72cf0-106">member</span><span class="sxs-lookup"><span data-stu-id="72cf0-106">Member</span></span>|<span data-ttu-id="72cf0-107">描述</span><span class="sxs-lookup"><span data-stu-id="72cf0-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="72cf0-108">指定將參數傳遞至方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="72cf0-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="72cf0-109">指定從方法傳回傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="72cf0-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="72cf0-110">指定參數為選擇項。</span><span class="sxs-lookup"><span data-stu-id="72cf0-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="72cf0-111">保留給 common language runtime 內部使用。</span><span class="sxs-lookup"><span data-stu-id="72cf0-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="72cf0-112">指定此參數具有預設值。</span><span class="sxs-lookup"><span data-stu-id="72cf0-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="72cf0-113">指定參數具有封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="72cf0-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="72cf0-114">未使用的。</span><span class="sxs-lookup"><span data-stu-id="72cf0-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72cf0-115">需求</span><span class="sxs-lookup"><span data-stu-id="72cf0-115">Requirements</span></span>  

 <span data-ttu-id="72cf0-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72cf0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72cf0-117">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="72cf0-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="72cf0-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72cf0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72cf0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72cf0-119">See also</span></span>

- [<span data-ttu-id="72cf0-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="72cf0-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
