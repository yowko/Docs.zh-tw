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
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450288"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="5d5a7-102">CorGenericParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="5d5a7-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="5d5a7-103">包含值，描述泛型型別的 <xref:System.Type> 參數，如[IMetaDataEmit2：:D efinegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)的呼叫中所使用。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d5a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d5a7-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="5d5a7-105">Members</span><span class="sxs-lookup"><span data-stu-id="5d5a7-105">Members</span></span>  
  
|<span data-ttu-id="5d5a7-106">成員</span><span class="sxs-lookup"><span data-stu-id="5d5a7-106">Member</span></span>|<span data-ttu-id="5d5a7-107">描述</span><span class="sxs-lookup"><span data-stu-id="5d5a7-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="5d5a7-108">參數變異數僅適用于介面和委派的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="5d5a7-109">表示缺少變異數。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="5d5a7-110">表示共變數。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="5d5a7-111">表示逆變性。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="5d5a7-112">特殊條件約束可以套用至任何 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="5d5a7-113">表示不會對 <xref:System.Type> 參數套用任何條件約束。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="5d5a7-114">表示 <xref:System.Type> 參數必須是參考型別。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="5d5a7-115">表示 <xref:System.Type> 參數必須是不能為 null 值的實值型別。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="5d5a7-116">表示 <xref:System.Type> 參數必須具有不採用任何參數的預設公用函式。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d5a7-117">需求</span><span class="sxs-lookup"><span data-stu-id="5d5a7-117">Requirements</span></span>  
 <span data-ttu-id="5d5a7-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d5a7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d5a7-119">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="5d5a7-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5d5a7-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d5a7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5a7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d5a7-121">See also</span></span>

- [<span data-ttu-id="5d5a7-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="5d5a7-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
