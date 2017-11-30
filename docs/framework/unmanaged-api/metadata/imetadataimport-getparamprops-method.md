---
title: "IMetaDataImport::GetParamProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3f36282df52b316bfa32c50c3fa9f55f829aa04e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="ab2c3-102">IMetaDataImport::GetParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="ab2c3-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="ab2c3-103">取得指定 ParamDef 語彙基元所參考參數的中繼資料值。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab2c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab2c3-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ab2c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab2c3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ab2c3-106">[in]ParamDef 語彙基元，代表要傳回的中繼資料的參數。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="ab2c3-107">[out]代表方法的 MethodDef 語彙基元的指標會接受參數。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="ab2c3-108">[out]方法引數清單中的參數序數位置。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="ab2c3-109">[out]要保存的參數名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ab2c3-110">[in]要求的大小，以寬字元`szName`。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ab2c3-111">[out]傳回的大小的寬字元`szName`。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="ab2c3-112">[out]任何參數相關聯的屬性旗標指標。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="ab2c3-113">[out]指向的旗標，指定參數是否為<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ab2c3-114">[out]參數所傳回的常數字串指標。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="ab2c3-115">[out]大小`ppValue`寬字元，或如果`ppValue`不會保存一個字串。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab2c3-116">需求</span><span class="sxs-lookup"><span data-stu-id="ab2c3-116">Requirements</span></span>  
 <span data-ttu-id="ab2c3-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab2c3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab2c3-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab2c3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab2c3-119">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ab2c3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab2c3-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab2c3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2c3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab2c3-121">See Also</span></span>  
 [<span data-ttu-id="ab2c3-122">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ab2c3-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ab2c3-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ab2c3-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
