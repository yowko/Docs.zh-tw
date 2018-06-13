---
title: IMetaDataImport::GetMethodProps 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4037ca42c5a66f075e949cd2035c1e7db510bb8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448904"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="f86cf-102">IMetaDataImport::GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="f86cf-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="f86cf-103">取得與指定 MethodDef 語彙基元所參考方法相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f86cf-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="f86cf-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f86cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="f86cf-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="f86cf-106">[in]表示要傳回的中繼資料的方法 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f86cf-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="f86cf-107">[out]代表實作方法的型別 TypeDef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="f86cf-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="f86cf-108">[out]方法的名稱緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="f86cf-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="f86cf-109">[in]要求的大小`szMethod`。</span><span class="sxs-lookup"><span data-stu-id="f86cf-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="f86cf-110">[out]中的寬字元大小的指標`szMethod`，如果發生截斷情形，實際的方法名稱中的寬字元數目。</span><span class="sxs-lookup"><span data-stu-id="f86cf-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="f86cf-111">[out]與方法相關聯的任何旗標指標。</span><span class="sxs-lookup"><span data-stu-id="f86cf-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="f86cf-112">[out]方法的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="f86cf-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="f86cf-113">[out]以位元組為單位的大小的指標`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="f86cf-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="f86cf-114">[out]方法的相對虛擬位址指標。</span><span class="sxs-lookup"><span data-stu-id="f86cf-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="f86cf-115">[out]任何方法的實作旗標指標。</span><span class="sxs-lookup"><span data-stu-id="f86cf-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f86cf-116">需求</span><span class="sxs-lookup"><span data-stu-id="f86cf-116">Requirements</span></span>  
 <span data-ttu-id="f86cf-117">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f86cf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f86cf-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f86cf-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f86cf-119">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f86cf-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f86cf-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f86cf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86cf-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f86cf-121">See Also</span></span>  
 [<span data-ttu-id="f86cf-122">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f86cf-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f86cf-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f86cf-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
