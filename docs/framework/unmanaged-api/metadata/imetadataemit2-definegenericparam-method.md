---
title: IMetaDataEmit2::DefineGenericParam 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b54f5bb47135bcf56c91cd07b916c959e75b9fb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745290"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="76a6b-102">IMetaDataEmit2::DefineGenericParam 方法</span><span class="sxs-lookup"><span data-stu-id="76a6b-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="76a6b-103">建立泛型類型參數的定義，並取得該泛型型別參數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76a6b-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="76a6b-104">Syntax</span></span>  
  
```  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76a6b-105">參數</span><span class="sxs-lookup"><span data-stu-id="76a6b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="76a6b-106">[in]`mdTypeDef`或`mdMethodDef`語彙基元，表示方法或建構函式為其定義的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="76a6b-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="76a6b-107">[in]泛型參數的索引。</span><span class="sxs-lookup"><span data-stu-id="76a6b-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="76a6b-108">[in]值為[CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)描述泛型參數類型的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="76a6b-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="76a6b-109">[in]參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="76a6b-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="76a6b-110">[in]此參數保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="76a6b-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="76a6b-111">[in]類型條件約束的零結尾的陣列。</span><span class="sxs-lookup"><span data-stu-id="76a6b-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="76a6b-112">陣列成員必須是`mdTypeDef`， `mdTypeRef`，或`mdTypeSpec`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76a6b-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="76a6b-113">[out]代表泛型參數的權杖。</span><span class="sxs-lookup"><span data-stu-id="76a6b-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76a6b-114">需求</span><span class="sxs-lookup"><span data-stu-id="76a6b-114">Requirements</span></span>  
 <span data-ttu-id="76a6b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76a6b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76a6b-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76a6b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76a6b-117">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="76a6b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76a6b-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76a6b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a6b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76a6b-119">See also</span></span>
- [<span data-ttu-id="76a6b-120">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="76a6b-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="76a6b-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="76a6b-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
