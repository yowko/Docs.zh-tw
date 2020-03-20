---
title: IMetaDataEmit::GetTokenFromTypeSpec 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 8c609d730297881c0ac20dca8569f0e9492638e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175716"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="84229-102">IMetaDataEmit::GetTokenFromTypeSpec 方法</span><span class="sxs-lookup"><span data-stu-id="84229-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="84229-103">使用指定的中繼資料簽名獲取類型的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="84229-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84229-104">語法</span><span class="sxs-lookup"><span data-stu-id="84229-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84229-105">參數</span><span class="sxs-lookup"><span data-stu-id="84229-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="84229-106">[在]正在定義的簽名。</span><span class="sxs-lookup"><span data-stu-id="84229-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="84229-107">[在]中的`pvSig`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="84229-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="84229-108">[出]分配的`mdTypeSpec`權杖。</span><span class="sxs-lookup"><span data-stu-id="84229-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84229-109">需求</span><span class="sxs-lookup"><span data-stu-id="84229-109">Requirements</span></span>  
 <span data-ttu-id="84229-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84229-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84229-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="84229-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84229-112">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="84229-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84229-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84229-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84229-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84229-114">See also</span></span>

- [<span data-ttu-id="84229-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="84229-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="84229-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="84229-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
