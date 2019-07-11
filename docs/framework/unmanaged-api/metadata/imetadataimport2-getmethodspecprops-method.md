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
ms.openlocfilehash: f7700236efe7b031866867f5ed859ba71683a8a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782289"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="8d733-102">IMetaDataImport2::GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="8d733-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="8d733-103">取得指定 methodspec Neobsahuje 所參考之方法的中繼資料簽章語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8d733-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d733-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d733-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="8d733-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d733-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="8d733-106">[in]表示方法具現化 methodspec Neobsahuje 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8d733-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="8d733-107">[out]表示方法定義的 MethodDef 或 MethodRef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="8d733-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="8d733-108">[out]二進位中繼資料簽章方法的指標。</span><span class="sxs-lookup"><span data-stu-id="8d733-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="8d733-109">[out]大小，以位元組為單位的`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="8d733-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d733-110">需求</span><span class="sxs-lookup"><span data-stu-id="8d733-110">Requirements</span></span>  
 <span data-ttu-id="8d733-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d733-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d733-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8d733-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d733-113">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d733-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d733-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d733-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d733-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d733-115">See also</span></span>

- [<span data-ttu-id="8d733-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8d733-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="8d733-117">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8d733-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
