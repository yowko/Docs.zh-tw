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
ms.openlocfilehash: 0eb4e9d713581cf32cec18bb02a6bd13542e517a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733176"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="defcb-102">IMetaDataImport::GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="defcb-102">IMetaDataImport::GetMethodProps Method</span></span>

<span data-ttu-id="defcb-103">取得與指定 MethodDef 語彙基元所參考方法相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="defcb-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="defcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="defcb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="defcb-105">參數</span><span class="sxs-lookup"><span data-stu-id="defcb-105">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="defcb-106">在MethodDef token，表示傳回中繼資料的方法。</span><span class="sxs-lookup"><span data-stu-id="defcb-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="defcb-107">擴展TypeDef token 的指標，表示執行方法的型別。</span><span class="sxs-lookup"><span data-stu-id="defcb-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="defcb-108">擴展具有方法名稱之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="defcb-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="defcb-109">在要求的大小 `szMethod` 。</span><span class="sxs-lookup"><span data-stu-id="defcb-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="defcb-110">擴展以寬字元為單位的大小指標 `szMethod` ，或在截斷的情況下，在方法名稱中的寬字元實際數目。</span><span class="sxs-lookup"><span data-stu-id="defcb-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="defcb-111">擴展與方法相關聯之任何旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="defcb-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="defcb-112">擴展方法的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="defcb-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="defcb-113">擴展大小的指標，以位元組為單位 `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="defcb-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="defcb-114">擴展方法的相對虛擬位址指標。</span><span class="sxs-lookup"><span data-stu-id="defcb-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="defcb-115">擴展方法之任何執行旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="defcb-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="defcb-116">需求</span><span class="sxs-lookup"><span data-stu-id="defcb-116">Requirements</span></span>  

 <span data-ttu-id="defcb-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="defcb-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="defcb-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="defcb-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="defcb-119">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="defcb-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="defcb-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="defcb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="defcb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="defcb-121">See also</span></span>

- [<span data-ttu-id="defcb-122">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="defcb-122">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="defcb-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="defcb-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
