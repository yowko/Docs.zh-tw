---
title: IMetaDataImport2::GetGenericParamConstraintProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3868b07ff01f2d1fec79537dd478a2d005f490f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778777"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="b58ee-102">IMetaDataImport2::GetGenericParamConstraintProps 方法</span><span class="sxs-lookup"><span data-stu-id="b58ee-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="b58ee-103">取得與指定的條件約束語彙基元所代表的泛型參數條件約束相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b58ee-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="b58ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b58ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="b58ee-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="b58ee-106">[in]泛型參數條件約束，要傳回的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b58ee-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="b58ee-107">[out]指標，代表泛型參數受限制的權杖。</span><span class="sxs-lookup"><span data-stu-id="b58ee-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="b58ee-108">[out]表示條件約束的 TypeDef、 TypeRef 或 TypeSpec 語彙基元的指標`ptGenericParam`。</span><span class="sxs-lookup"><span data-stu-id="b58ee-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b58ee-109">需求</span><span class="sxs-lookup"><span data-stu-id="b58ee-109">Requirements</span></span>  
 <span data-ttu-id="b58ee-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b58ee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b58ee-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b58ee-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b58ee-112">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b58ee-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b58ee-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b58ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58ee-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b58ee-114">See also</span></span>

- [<span data-ttu-id="b58ee-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="b58ee-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="b58ee-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="b58ee-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
