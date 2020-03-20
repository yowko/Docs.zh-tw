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
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176171"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="1b74b-102">CorGenericParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="1b74b-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="1b74b-103">包含描述泛型型別的<xref:System.Type>參數的值，如調用[IMetaDataEmit2：:DefinegenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)中使用的。</span><span class="sxs-lookup"><span data-stu-id="1b74b-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b74b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b74b-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1b74b-105">成員</span><span class="sxs-lookup"><span data-stu-id="1b74b-105">Members</span></span>  
  
|<span data-ttu-id="1b74b-106">member</span><span class="sxs-lookup"><span data-stu-id="1b74b-106">Member</span></span>|<span data-ttu-id="1b74b-107">描述</span><span class="sxs-lookup"><span data-stu-id="1b74b-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="1b74b-108">參數方差僅適用于介面和委託的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="1b74b-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="1b74b-109">指示不存在方差。</span><span class="sxs-lookup"><span data-stu-id="1b74b-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="1b74b-110">表示共變數。</span><span class="sxs-lookup"><span data-stu-id="1b74b-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="1b74b-111">表示不差異。</span><span class="sxs-lookup"><span data-stu-id="1b74b-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="1b74b-112">特殊約束可以應用於任何<xref:System.Type>參數。</span><span class="sxs-lookup"><span data-stu-id="1b74b-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="1b74b-113">指示沒有約束應用於參數<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="1b74b-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="1b74b-114">指示參數<xref:System.Type>必須是參考型別。</span><span class="sxs-lookup"><span data-stu-id="1b74b-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="1b74b-115">指示參數<xref:System.Type>必須是不能為空值的數值型別。</span><span class="sxs-lookup"><span data-stu-id="1b74b-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="1b74b-116">指示<xref:System.Type>參數必須具有不需要參數的預設公共建構函式。</span><span class="sxs-lookup"><span data-stu-id="1b74b-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b74b-117">需求</span><span class="sxs-lookup"><span data-stu-id="1b74b-117">Requirements</span></span>  
 <span data-ttu-id="1b74b-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b74b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b74b-119">**標題：** 科爾赫德</span><span class="sxs-lookup"><span data-stu-id="1b74b-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1b74b-120">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b74b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b74b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b74b-121">See also</span></span>

- [<span data-ttu-id="1b74b-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="1b74b-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
