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
ms.openlocfilehash: 4a258ce9121a287929ca5bc39c480f1ca2596e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437470"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="348cf-102">IMetaDataImport::GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="348cf-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="348cf-103">取得與指定 MethodDef 語彙基元所參考方法相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="348cf-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="348cf-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="348cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="348cf-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="348cf-106">在MethodDef token，表示要傳回中繼資料的方法。</span><span class="sxs-lookup"><span data-stu-id="348cf-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="348cf-107">脫銷TypeDef token 的指標，表示可執行方法的類型。</span><span class="sxs-lookup"><span data-stu-id="348cf-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="348cf-108">脫銷具有方法名稱之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="348cf-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="348cf-109">在要求的 `szMethod`大小。</span><span class="sxs-lookup"><span data-stu-id="348cf-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="348cf-110">脫銷`szMethod`的寬字元大小指標，或在截斷的情況下，方法名稱中的寬字元實際數目。</span><span class="sxs-lookup"><span data-stu-id="348cf-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="348cf-111">脫銷與方法相關聯之任何旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="348cf-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="348cf-112">脫銷方法之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="348cf-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="348cf-113">脫銷以位元組為單位的 `ppvSigBlob`大小的指標。</span><span class="sxs-lookup"><span data-stu-id="348cf-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="348cf-114">脫銷方法之相對虛擬位址的指標。</span><span class="sxs-lookup"><span data-stu-id="348cf-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="348cf-115">脫銷方法之任何執行旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="348cf-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="348cf-116">需求</span><span class="sxs-lookup"><span data-stu-id="348cf-116">Requirements</span></span>  
 <span data-ttu-id="348cf-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="348cf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="348cf-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="348cf-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="348cf-119">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="348cf-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="348cf-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="348cf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348cf-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="348cf-121">See also</span></span>

- [<span data-ttu-id="348cf-122">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="348cf-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="348cf-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="348cf-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
