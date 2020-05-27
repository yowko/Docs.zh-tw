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
ms.openlocfilehash: 6e24db7da7abbdb597b8ff64515e8053667af3ff
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008764"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="c8fd6-102">IMetaDataEmit::SetCustomAttributeValue 方法</span><span class="sxs-lookup"><span data-stu-id="c8fd6-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="c8fd6-103">設定或更新先前呼叫[IMetaDataEmit：:D efinecustomattribute](imetadataemit-definecustomattribute-method.md)所定義的自訂屬性值。</span><span class="sxs-lookup"><span data-stu-id="c8fd6-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8fd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8fd6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8fd6-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8fd6-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="c8fd6-106">在目標自訂屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="c8fd6-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="c8fd6-107">在包含自訂屬性之陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="c8fd6-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="c8fd6-108">在自訂屬性的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c8fd6-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8fd6-109">需求</span><span class="sxs-lookup"><span data-stu-id="c8fd6-109">Requirements</span></span>  
 <span data-ttu-id="c8fd6-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8fd6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8fd6-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c8fd6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8fd6-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c8fd6-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8fd6-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8fd6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fd6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8fd6-114">See also</span></span>

- [<span data-ttu-id="c8fd6-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c8fd6-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c8fd6-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c8fd6-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
