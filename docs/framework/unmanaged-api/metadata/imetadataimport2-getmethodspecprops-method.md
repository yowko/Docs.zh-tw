---
title: IMetaDataImport2::GetMethodSpecProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69af794d5405894d24f0d7545613a0e85ca3ec6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574010"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="08da3-102">IMetaDataImport2::GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="08da3-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="08da3-103">取得指定 methodspec Neobsahuje 所參考之方法的中繼資料簽章語彙基元。</span><span class="sxs-lookup"><span data-stu-id="08da3-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08da3-104">語法</span><span class="sxs-lookup"><span data-stu-id="08da3-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="08da3-105">參數</span><span class="sxs-lookup"><span data-stu-id="08da3-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="08da3-106">[in]表示方法具現化 methodspec Neobsahuje 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="08da3-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="08da3-107">[out]表示方法定義的 MethodDef 或 MethodRef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="08da3-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="08da3-108">[out]二進位中繼資料簽章方法的指標。</span><span class="sxs-lookup"><span data-stu-id="08da3-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="08da3-109">[out]大小，以位元組為單位的`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="08da3-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08da3-110">需求</span><span class="sxs-lookup"><span data-stu-id="08da3-110">Requirements</span></span>  
 <span data-ttu-id="08da3-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08da3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08da3-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08da3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08da3-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="08da3-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08da3-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08da3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08da3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08da3-115">See also</span></span>
- [<span data-ttu-id="08da3-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="08da3-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="08da3-117">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="08da3-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
