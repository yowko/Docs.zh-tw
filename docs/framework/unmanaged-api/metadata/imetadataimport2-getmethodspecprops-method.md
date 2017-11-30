---
title: "IMetaDataImport2::GetMethodSpecProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetMethodSpecProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b07e79f3990782e18ffdc57e9bd75a0b62765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="b6d48-102">IMetaDataImport2::GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="b6d48-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="b6d48-103">取得所指定的 MethodSpec 參考方法的中繼資料簽章語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b6d48-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d48-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6d48-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6d48-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6d48-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="b6d48-106">[in]MethodSpec 語彙基元，代表方法的具現化。</span><span class="sxs-lookup"><span data-stu-id="b6d48-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="b6d48-107">[out]代表方法定義 MethodDef 或 MethodRef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="b6d48-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="b6d48-108">[out]方法的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="b6d48-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="b6d48-109">[out]大小，以位元組為單位的`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="b6d48-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d48-110">需求</span><span class="sxs-lookup"><span data-stu-id="b6d48-110">Requirements</span></span>  
 <span data-ttu-id="b6d48-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6d48-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6d48-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6d48-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6d48-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6d48-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6d48-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6d48-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d48-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6d48-115">See Also</span></span>  
 [<span data-ttu-id="b6d48-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="b6d48-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="b6d48-117">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="b6d48-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
