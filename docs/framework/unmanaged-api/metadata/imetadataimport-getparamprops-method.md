---
title: IMetaDataImport::GetParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 697a59d80e152fb78164491c2a0eaaa8707f8914
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745916"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="49d67-102">IMetaDataImport::GetParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="49d67-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="49d67-103">取得指定 ParamDef 語彙基元所參考參數的中繼資料值。</span><span class="sxs-lookup"><span data-stu-id="49d67-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d67-104">語法</span><span class="sxs-lookup"><span data-stu-id="49d67-104">Syntax</span></span>  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49d67-105">參數</span><span class="sxs-lookup"><span data-stu-id="49d67-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="49d67-106">[in]ParamDef 語彙基元，表示要傳回的中繼資料的參數。</span><span class="sxs-lookup"><span data-stu-id="49d67-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="49d67-107">[out]表示方法的 MethodDef 語彙基元的指標，會接受參數。</span><span class="sxs-lookup"><span data-stu-id="49d67-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="49d67-108">[out]方法引數清單中的參數序數位置。</span><span class="sxs-lookup"><span data-stu-id="49d67-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="49d67-109">[out]若要保留的參數名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="49d67-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="49d67-110">[in]所要求的大小，以寬字元為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="49d67-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="49d67-111">[out]寬字元在傳回的大小`szName`。</span><span class="sxs-lookup"><span data-stu-id="49d67-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="49d67-112">[out]任何與參數相關聯的屬性旗標指標。</span><span class="sxs-lookup"><span data-stu-id="49d67-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="49d67-113">這是位元遮罩`CorParamAttr`值。</span><span class="sxs-lookup"><span data-stu-id="49d67-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="49d67-114">[out]參數是以旗標，指定指標<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="49d67-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="49d67-115">[out]參數所傳回的常數字串指標。</span><span class="sxs-lookup"><span data-stu-id="49d67-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="49d67-116">[out]大小`ppValue`寬字元，或零，如果`ppValue`不會保留為字串。</span><span class="sxs-lookup"><span data-stu-id="49d67-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49d67-117">備註</span><span class="sxs-lookup"><span data-stu-id="49d67-117">Remarks</span></span>

<span data-ttu-id="49d67-118">中的值序列`pulSequence`參數 1 為開頭。</span><span class="sxs-lookup"><span data-stu-id="49d67-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="49d67-119">傳回值具有 0 的序號。</span><span class="sxs-lookup"><span data-stu-id="49d67-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="49d67-120">需求</span><span class="sxs-lookup"><span data-stu-id="49d67-120">Requirements</span></span>  
 <span data-ttu-id="49d67-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49d67-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d67-122">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="49d67-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49d67-123">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="49d67-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49d67-124">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d67-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d67-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49d67-125">See also</span></span>
- [<span data-ttu-id="49d67-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="49d67-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="49d67-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="49d67-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
