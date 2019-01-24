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
ms.openlocfilehash: c4e4b163cc783ccd01bc406789f5bf92448c697c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685525"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="950ae-102">IMetaDataImport::GetParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="950ae-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="950ae-103">取得指定 ParamDef 語彙基元所參考參數的中繼資料值。</span><span class="sxs-lookup"><span data-stu-id="950ae-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="950ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="950ae-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="950ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="950ae-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="950ae-106">[in]ParamDef 語彙基元，表示要傳回的中繼資料的參數。</span><span class="sxs-lookup"><span data-stu-id="950ae-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="950ae-107">[out]表示方法的 MethodDef 語彙基元的指標，會接受參數。</span><span class="sxs-lookup"><span data-stu-id="950ae-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="950ae-108">[out]方法引數清單中的參數序數位置。</span><span class="sxs-lookup"><span data-stu-id="950ae-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="950ae-109">[out]若要保留的參數名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="950ae-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="950ae-110">[in]所要求的大小，以寬字元為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="950ae-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="950ae-111">[out]寬字元在傳回的大小`szName`。</span><span class="sxs-lookup"><span data-stu-id="950ae-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="950ae-112">[out]任何與參數相關聯的屬性旗標指標。</span><span class="sxs-lookup"><span data-stu-id="950ae-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="950ae-113">[out]參數是以旗標，指定指標<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="950ae-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="950ae-114">[out]參數所傳回的常數字串指標。</span><span class="sxs-lookup"><span data-stu-id="950ae-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="950ae-115">[out]大小`ppValue`寬字元，或零，如果`ppValue`不會保留為字串。</span><span class="sxs-lookup"><span data-stu-id="950ae-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="950ae-116">需求</span><span class="sxs-lookup"><span data-stu-id="950ae-116">Requirements</span></span>  
 <span data-ttu-id="950ae-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="950ae-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="950ae-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="950ae-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="950ae-119">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="950ae-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="950ae-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="950ae-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950ae-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="950ae-121">See also</span></span>
- [<span data-ttu-id="950ae-122">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="950ae-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="950ae-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="950ae-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
