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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d07c6de47038d5c52d76ad8ca8e0a5684551d59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491463"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="64fdb-102">CorParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="64fdb-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="64fdb-103">包含值，這些值描述方法參數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="64fdb-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64fdb-104">語法</span><span class="sxs-lookup"><span data-stu-id="64fdb-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="64fdb-105">成員</span><span class="sxs-lookup"><span data-stu-id="64fdb-105">Members</span></span>  
  
|<span data-ttu-id="64fdb-106">成員</span><span class="sxs-lookup"><span data-stu-id="64fdb-106">Member</span></span>|<span data-ttu-id="64fdb-107">描述</span><span class="sxs-lookup"><span data-stu-id="64fdb-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="64fdb-108">指定此參數會傳遞至方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="64fdb-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="64fdb-109">指定參數傳遞從方法傳回。</span><span class="sxs-lookup"><span data-stu-id="64fdb-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="64fdb-110">指定的參數為選擇性。</span><span class="sxs-lookup"><span data-stu-id="64fdb-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="64fdb-111">保留供內部使用的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="64fdb-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="64fdb-112">指定參數有預設值。</span><span class="sxs-lookup"><span data-stu-id="64fdb-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="64fdb-113">指定參數的封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="64fdb-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="64fdb-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="64fdb-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64fdb-115">需求</span><span class="sxs-lookup"><span data-stu-id="64fdb-115">Requirements</span></span>  
 <span data-ttu-id="64fdb-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64fdb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64fdb-117">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="64fdb-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="64fdb-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64fdb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fdb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64fdb-119">See also</span></span>
- [<span data-ttu-id="64fdb-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="64fdb-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
