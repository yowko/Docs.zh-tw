---
title: CorGenericParamAttr 列舉
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf73f382c1da15e0285ee95be9e8bce39575ae0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557355"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="33ceb-102">CorGenericParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="33ceb-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="33ceb-103">包含描述值<xref:System.Type>呼叫中使用的泛型類型參數[IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)。</span><span class="sxs-lookup"><span data-stu-id="33ceb-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ceb-104">語法</span><span class="sxs-lookup"><span data-stu-id="33ceb-104">Syntax</span></span>  
  
```  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="33ceb-105">成員</span><span class="sxs-lookup"><span data-stu-id="33ceb-105">Members</span></span>  
  
|<span data-ttu-id="33ceb-106">成員</span><span class="sxs-lookup"><span data-stu-id="33ceb-106">Member</span></span>|<span data-ttu-id="33ceb-107">描述</span><span class="sxs-lookup"><span data-stu-id="33ceb-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="33ceb-108">參數的變異數只適用於介面和委派的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="33ceb-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="33ceb-109">表示變異數不存在。</span><span class="sxs-lookup"><span data-stu-id="33ceb-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="33ceb-110">表示共異變數。</span><span class="sxs-lookup"><span data-stu-id="33ceb-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="33ceb-111">表示反變數。</span><span class="sxs-lookup"><span data-stu-id="33ceb-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="33ceb-112">特殊條件約束可以套用至任何<xref:System.Type>參數。</span><span class="sxs-lookup"><span data-stu-id="33ceb-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="33ceb-113">指出沒有條件約束套用至<xref:System.Type>參數。</span><span class="sxs-lookup"><span data-stu-id="33ceb-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="33ceb-114">表示<xref:System.Type>參數必須是參考型別。</span><span class="sxs-lookup"><span data-stu-id="33ceb-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="33ceb-115">表示<xref:System.Type>參數必須是實值類型不得為 null 的值。</span><span class="sxs-lookup"><span data-stu-id="33ceb-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="33ceb-116">表示<xref:System.Type>參數必須要有的預設公用建構函式不接受任何參數。</span><span class="sxs-lookup"><span data-stu-id="33ceb-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33ceb-117">需求</span><span class="sxs-lookup"><span data-stu-id="33ceb-117">Requirements</span></span>  
 <span data-ttu-id="33ceb-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33ceb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ceb-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="33ceb-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="33ceb-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33ceb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ceb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33ceb-121">See also</span></span>
- [<span data-ttu-id="33ceb-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="33ceb-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
