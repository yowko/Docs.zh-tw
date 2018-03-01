---
title: "CorParamAttr 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 87afe125536473f99053db7d2fd4ae61fa4017ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="52b0d-102">CorParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="52b0d-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="52b0d-103">包含值，這些值描述方法參數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="52b0d-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="52b0d-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="52b0d-105">成員</span><span class="sxs-lookup"><span data-stu-id="52b0d-105">Members</span></span>  
  
|<span data-ttu-id="52b0d-106">成員</span><span class="sxs-lookup"><span data-stu-id="52b0d-106">Member</span></span>|<span data-ttu-id="52b0d-107">描述</span><span class="sxs-lookup"><span data-stu-id="52b0d-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="52b0d-108">指定的參數會傳遞至方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="52b0d-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="52b0d-109">指定的參數傳遞從方法傳回。</span><span class="sxs-lookup"><span data-stu-id="52b0d-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="52b0d-110">指定是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="52b0d-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="52b0d-111">保留供內部使用的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="52b0d-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="52b0d-112">指定參數有預設值。</span><span class="sxs-lookup"><span data-stu-id="52b0d-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="52b0d-113">指定的參數有封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="52b0d-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="52b0d-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="52b0d-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52b0d-115">需求</span><span class="sxs-lookup"><span data-stu-id="52b0d-115">Requirements</span></span>  
 <span data-ttu-id="52b0d-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52b0d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52b0d-117">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="52b0d-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="52b0d-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52b0d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b0d-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="52b0d-119">See Also</span></span>  
 [<span data-ttu-id="52b0d-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="52b0d-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
