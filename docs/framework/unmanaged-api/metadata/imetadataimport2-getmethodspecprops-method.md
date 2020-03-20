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
ms.openlocfilehash: 0bfbfec930c193ea05a01bd5bd9f46d2ec6714b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175287"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="2aa10-102">IMetaDataImport2::GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="2aa10-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="2aa10-103">獲取指定方法Spec權杖引用的方法的中繼資料簽名。</span><span class="sxs-lookup"><span data-stu-id="2aa10-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa10-104">語法</span><span class="sxs-lookup"><span data-stu-id="2aa10-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2aa10-105">參數</span><span class="sxs-lookup"><span data-stu-id="2aa10-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="2aa10-106">[在]表示方法具現化的 MethodSpec 權杖。</span><span class="sxs-lookup"><span data-stu-id="2aa10-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="2aa10-107">[出]指向表示方法定義的方法Def 或方法Ref 權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="2aa10-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="2aa10-108">[出]指向方法的二進位中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="2aa10-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="2aa10-109">[出]的大小（以位元組為單位）的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="2aa10-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aa10-110">需求</span><span class="sxs-lookup"><span data-stu-id="2aa10-110">Requirements</span></span>  
 <span data-ttu-id="2aa10-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2aa10-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aa10-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="2aa10-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2aa10-113">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2aa10-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2aa10-114">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aa10-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa10-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2aa10-115">See also</span></span>

- [<span data-ttu-id="2aa10-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2aa10-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="2aa10-117">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2aa10-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
