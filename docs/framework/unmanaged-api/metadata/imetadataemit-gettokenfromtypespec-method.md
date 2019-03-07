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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff240a80d2910dcb050cc022257c6eba166bbdc5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465929"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="01ea0-102">IMetaDataEmit::GetTokenFromTypeSpec 方法</span><span class="sxs-lookup"><span data-stu-id="01ea0-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="01ea0-103">取得具有指定之中繼資料簽章的類型中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="01ea0-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ea0-104">語法</span><span class="sxs-lookup"><span data-stu-id="01ea0-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01ea0-105">參數</span><span class="sxs-lookup"><span data-stu-id="01ea0-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="01ea0-106">[in]正在定義的簽章。</span><span class="sxs-lookup"><span data-stu-id="01ea0-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="01ea0-107">[in]中的位元組計數`pvSig`。</span><span class="sxs-lookup"><span data-stu-id="01ea0-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="01ea0-108">[out]`mdTypeSpec`指派權杖。</span><span class="sxs-lookup"><span data-stu-id="01ea0-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01ea0-109">需求</span><span class="sxs-lookup"><span data-stu-id="01ea0-109">Requirements</span></span>  
 <span data-ttu-id="01ea0-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01ea0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01ea0-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="01ea0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01ea0-112">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="01ea0-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01ea0-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01ea0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ea0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01ea0-114">See also</span></span>
- [<span data-ttu-id="01ea0-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="01ea0-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="01ea0-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="01ea0-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
