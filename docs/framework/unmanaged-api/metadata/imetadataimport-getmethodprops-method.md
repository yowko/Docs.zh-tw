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
ms.openlocfilehash: 3c7c3525f2f8753241c9a206e4cf5e552bf06efe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503618"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="abfd5-102">IMetaDataImport::GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="abfd5-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="abfd5-103">取得與指定 MethodDef 語彙基元所參考方法相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="abfd5-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abfd5-104">語法</span><span class="sxs-lookup"><span data-stu-id="abfd5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="abfd5-105">參數</span><span class="sxs-lookup"><span data-stu-id="abfd5-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="abfd5-106">在MethodDef token，表示要傳回中繼資料的方法。</span><span class="sxs-lookup"><span data-stu-id="abfd5-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="abfd5-107">脫銷TypeDef token 的指標，表示可執行方法的類型。</span><span class="sxs-lookup"><span data-stu-id="abfd5-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="abfd5-108">脫銷具有方法名稱之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="abfd5-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="abfd5-109">在要求的大小 `szMethod` 。</span><span class="sxs-lookup"><span data-stu-id="abfd5-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="abfd5-110">脫銷大小的指標，以寬字元為單位 `szMethod` ，或在截斷的情況下，為方法名稱中的寬字元實際數目。</span><span class="sxs-lookup"><span data-stu-id="abfd5-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="abfd5-111">脫銷與方法相關聯之任何旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="abfd5-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="abfd5-112">脫銷方法之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="abfd5-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="abfd5-113">脫銷大小的指標，以位元組為單位 `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="abfd5-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="abfd5-114">脫銷方法之相對虛擬位址的指標。</span><span class="sxs-lookup"><span data-stu-id="abfd5-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="abfd5-115">脫銷方法之任何執行旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="abfd5-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abfd5-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="abfd5-116">Requirements</span></span>  
 <span data-ttu-id="abfd5-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abfd5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abfd5-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="abfd5-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abfd5-119">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="abfd5-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="abfd5-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abfd5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abfd5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abfd5-121">See also</span></span>

- [<span data-ttu-id="abfd5-122">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="abfd5-122">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="abfd5-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="abfd5-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
