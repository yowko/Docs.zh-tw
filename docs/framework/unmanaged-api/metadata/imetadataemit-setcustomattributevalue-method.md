---
title: IMetaDataEmit::SetCustomAttributeValue 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a1f248cf800e9c2bf17d7849e449287cfc493f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737211"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="eebf5-102">IMetaDataEmit::SetCustomAttributeValue 方法</span><span class="sxs-lookup"><span data-stu-id="eebf5-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="eebf5-103">設定或更新先前呼叫所定義的自訂屬性的值[imetadataemit:: Definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)。</span><span class="sxs-lookup"><span data-stu-id="eebf5-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eebf5-104">語法</span><span class="sxs-lookup"><span data-stu-id="eebf5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eebf5-105">參數</span><span class="sxs-lookup"><span data-stu-id="eebf5-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="eebf5-106">[in]目標的自訂屬性的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="eebf5-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="eebf5-107">[in]包含自訂屬性陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="eebf5-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="eebf5-108">[in]以位元組為單位，自訂屬性的大小。</span><span class="sxs-lookup"><span data-stu-id="eebf5-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eebf5-109">需求</span><span class="sxs-lookup"><span data-stu-id="eebf5-109">Requirements</span></span>  
 <span data-ttu-id="eebf5-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eebf5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eebf5-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eebf5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eebf5-112">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eebf5-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eebf5-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eebf5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebf5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eebf5-114">See also</span></span>

- [<span data-ttu-id="eebf5-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="eebf5-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="eebf5-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="eebf5-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
