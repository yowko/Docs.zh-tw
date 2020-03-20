---
title: IMetaDataEmit2::SetGenericParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: fd7f149e806727d849cdceb3ffbc5dc7392fcf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177416"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="efd15-102">IMetaDataEmit2::SetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="efd15-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="efd15-103">設置指定權杖引用的泛型參數定義的屬性值。</span><span class="sxs-lookup"><span data-stu-id="efd15-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd15-104">語法</span><span class="sxs-lookup"><span data-stu-id="efd15-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efd15-105">參數</span><span class="sxs-lookup"><span data-stu-id="efd15-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="efd15-106">[在]要為其設置值的泛型參數定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="efd15-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="efd15-107">[在]描述泛型參數類型的[CorgenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)枚舉的值。</span><span class="sxs-lookup"><span data-stu-id="efd15-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="efd15-108">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="efd15-108">[in] Optional.</span></span> <span data-ttu-id="efd15-109">要為其設置值的參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="efd15-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="efd15-110">[在]保留以供將來擴展。</span><span class="sxs-lookup"><span data-stu-id="efd15-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="efd15-111">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="efd15-111">[in] Optional.</span></span> <span data-ttu-id="efd15-112">類型約束的零端接陣列。</span><span class="sxs-lookup"><span data-stu-id="efd15-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="efd15-113">陣列成員必須是`mdTypeDef`，`mdTypeRef`或`mdTypeSpec`中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="efd15-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd15-114">需求</span><span class="sxs-lookup"><span data-stu-id="efd15-114">Requirements</span></span>  
 <span data-ttu-id="efd15-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="efd15-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd15-116">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="efd15-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efd15-117">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="efd15-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="efd15-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd15-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd15-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efd15-119">See also</span></span>

- [<span data-ttu-id="efd15-120">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="efd15-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="efd15-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="efd15-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
