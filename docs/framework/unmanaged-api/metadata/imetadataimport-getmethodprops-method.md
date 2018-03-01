---
title: "IMetaDataImport::GetMethodProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e4e0ae7dfed4b13ea83e16d6380443c9d1b72b06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="59b67-102">IMetaDataImport::GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="59b67-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="59b67-103">取得與指定 MethodDef 語彙基元所參考方法相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="59b67-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b67-104">語法</span><span class="sxs-lookup"><span data-stu-id="59b67-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59b67-105">參數</span><span class="sxs-lookup"><span data-stu-id="59b67-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="59b67-106">[in]表示要傳回的中繼資料的方法 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="59b67-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="59b67-107">[out]代表實作方法的型別 TypeDef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="59b67-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="59b67-108">[out]方法的名稱緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="59b67-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="59b67-109">[in]要求的大小`szMethod`。</span><span class="sxs-lookup"><span data-stu-id="59b67-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="59b67-110">[out]中的寬字元大小的指標`szMethod`，如果發生截斷情形，實際的方法名稱中的寬字元數目。</span><span class="sxs-lookup"><span data-stu-id="59b67-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="59b67-111">[out]與方法相關聯的任何旗標指標。</span><span class="sxs-lookup"><span data-stu-id="59b67-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="59b67-112">[out]方法的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="59b67-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="59b67-113">[out]以位元組為單位的大小的指標`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="59b67-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="59b67-114">[out]方法的相對虛擬位址指標。</span><span class="sxs-lookup"><span data-stu-id="59b67-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="59b67-115">[out]任何方法的實作旗標指標。</span><span class="sxs-lookup"><span data-stu-id="59b67-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59b67-116">需求</span><span class="sxs-lookup"><span data-stu-id="59b67-116">Requirements</span></span>  
 <span data-ttu-id="59b67-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59b67-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59b67-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="59b67-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59b67-119">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="59b67-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59b67-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59b67-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b67-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="59b67-121">See Also</span></span>  
 [<span data-ttu-id="59b67-122">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="59b67-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="59b67-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="59b67-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
