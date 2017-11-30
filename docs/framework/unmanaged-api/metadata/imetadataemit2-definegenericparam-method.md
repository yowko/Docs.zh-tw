---
title: "IMetaDataEmit2::DefineGenericParam 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineGenericParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 737e57b86e74cc7e4668589d16c2e2cb351162bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="ee5d8-102">IMetaDataEmit2::DefineGenericParam 方法</span><span class="sxs-lookup"><span data-stu-id="ee5d8-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="ee5d8-103">建立泛型類型參數，並取得該泛型型別參數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee5d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee5d8-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ee5d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee5d8-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ee5d8-106">[in]`mdTypeDef`或`mdMethodDef`表示的方法或建構函式定義的泛型參數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="ee5d8-107">[in]泛型參數的索引。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="ee5d8-108">[in]值為[CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)描述對泛型參數類型的列舉。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="ee5d8-109">[in]參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="ee5d8-110">[in]這個參數被保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="ee5d8-111">[in]類型條件約束的零結尾的陣列。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="ee5d8-112">必須是陣列成員`mdTypeDef`， `mdTypeRef`，或`mdTypeSpec`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="ee5d8-113">[out]代表泛型參數的權杖。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee5d8-114">需求</span><span class="sxs-lookup"><span data-stu-id="ee5d8-114">Requirements</span></span>  
 <span data-ttu-id="ee5d8-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee5d8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee5d8-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee5d8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee5d8-117">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ee5d8-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee5d8-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee5d8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5d8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee5d8-119">See Also</span></span>  
 [<span data-ttu-id="ee5d8-120">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ee5d8-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="ee5d8-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ee5d8-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
