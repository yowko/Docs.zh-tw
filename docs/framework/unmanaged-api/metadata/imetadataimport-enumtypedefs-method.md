---
title: IMetaDataImport::EnumTypeDefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450002"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="f1b55-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="f1b55-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="f1b55-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f1b55-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1b55-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1b55-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1b55-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1b55-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f1b55-106">[out] A pointer to the new enumerator.</span><span class="sxs-lookup"><span data-stu-id="f1b55-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="f1b55-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="f1b55-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="f1b55-108">[in] The array used to store the TypeDef tokens.</span><span class="sxs-lookup"><span data-stu-id="f1b55-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f1b55-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="f1b55-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="f1b55-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="f1b55-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1b55-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1b55-111">Return Value</span></span>  
  
|<span data-ttu-id="f1b55-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1b55-112">HRESULT</span></span>|<span data-ttu-id="f1b55-113">描述</span><span class="sxs-lookup"><span data-stu-id="f1b55-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f1b55-114">`EnumTypeDefs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="f1b55-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f1b55-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="f1b55-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f1b55-116">In that case, `pcTypeDefs` is zero.</span><span class="sxs-lookup"><span data-stu-id="f1b55-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1b55-117">備註</span><span class="sxs-lookup"><span data-stu-id="f1b55-117">Remarks</span></span>  
 <span data-ttu-id="f1b55-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span><span class="sxs-lookup"><span data-stu-id="f1b55-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1b55-119">需求</span><span class="sxs-lookup"><span data-stu-id="f1b55-119">Requirements</span></span>  
 <span data-ttu-id="f1b55-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1b55-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1b55-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1b55-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1b55-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1b55-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1b55-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1b55-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b55-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="f1b55-124">See also</span></span>

- [<span data-ttu-id="f1b55-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f1b55-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f1b55-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f1b55-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
