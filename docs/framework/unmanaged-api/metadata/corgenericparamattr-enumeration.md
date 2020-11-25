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
ms.openlocfilehash: ea50430c3ae6cef9b47880bcb8ad969f62ce9c39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704906"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="af877-102">CorGenericParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="af877-102">CorGenericParamAttr Enumeration</span></span>

<span data-ttu-id="af877-103">包含值，這些值會描述 <xref:System.Type> 泛型型別的參數，如同用在 [IMetaDataEmit2：:D efinegenericparam](imetadataemit2-definegenericparam-method.md)的呼叫中。</span><span class="sxs-lookup"><span data-stu-id="af877-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af877-104">語法</span><span class="sxs-lookup"><span data-stu-id="af877-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="af877-105">成員</span><span class="sxs-lookup"><span data-stu-id="af877-105">Members</span></span>  
  
|<span data-ttu-id="af877-106">member</span><span class="sxs-lookup"><span data-stu-id="af877-106">Member</span></span>|<span data-ttu-id="af877-107">描述</span><span class="sxs-lookup"><span data-stu-id="af877-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="af877-108">參數變異數只適用于介面和委派的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="af877-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="af877-109">指出沒有變異數。</span><span class="sxs-lookup"><span data-stu-id="af877-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="af877-110">表示共變數。</span><span class="sxs-lookup"><span data-stu-id="af877-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="af877-111">表示反變數。</span><span class="sxs-lookup"><span data-stu-id="af877-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="af877-112">特殊條件約束可以套用至任何 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="af877-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="af877-113">指出沒有任何條件約束適用于 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="af877-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="af877-114">指出 <xref:System.Type> 參數必須是參考型別。</span><span class="sxs-lookup"><span data-stu-id="af877-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="af877-115">指出 <xref:System.Type> 參數必須是不能是 null 值的實值型別。</span><span class="sxs-lookup"><span data-stu-id="af877-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="af877-116">指出 <xref:System.Type> 參數必須有不採用任何參數的預設公用函數。</span><span class="sxs-lookup"><span data-stu-id="af877-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af877-117">需求</span><span class="sxs-lookup"><span data-stu-id="af877-117">Requirements</span></span>  

 <span data-ttu-id="af877-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af877-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af877-119">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="af877-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="af877-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af877-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af877-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af877-121">See also</span></span>

- [<span data-ttu-id="af877-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="af877-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
