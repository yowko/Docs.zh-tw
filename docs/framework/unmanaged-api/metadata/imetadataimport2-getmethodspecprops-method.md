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
ms.openlocfilehash: 079d9245526ff7914d1cbd6a91f0f2d96a690af5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490441"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="ea5b7-102">IMetaDataImport2::GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="ea5b7-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="ea5b7-103">取得指定的 MethodSpec token 所參考之方法的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="ea5b7-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea5b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea5b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="ea5b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea5b7-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="ea5b7-106">在一個 MethodSpec token，代表方法的具現化。</span><span class="sxs-lookup"><span data-stu-id="ea5b7-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="ea5b7-107">脫銷MethodDef 或 MethodRef token 的指標，表示方法定義。</span><span class="sxs-lookup"><span data-stu-id="ea5b7-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="ea5b7-108">脫銷方法之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="ea5b7-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="ea5b7-109">脫銷的大小（以位元組為單位） `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="ea5b7-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea5b7-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="ea5b7-110">Requirements</span></span>  
 <span data-ttu-id="ea5b7-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea5b7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea5b7-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ea5b7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea5b7-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ea5b7-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea5b7-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea5b7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea5b7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea5b7-115">See also</span></span>

- [<span data-ttu-id="ea5b7-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ea5b7-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="ea5b7-117">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ea5b7-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
