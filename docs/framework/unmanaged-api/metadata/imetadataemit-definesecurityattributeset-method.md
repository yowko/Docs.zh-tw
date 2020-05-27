---
title: IMetaDataEmit::DefineSecurityAttributeSet 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: c33ede841324820da16e33d35bbf5e8f8e75924f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009362"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="31f54-102">IMetaDataEmit::DefineSecurityAttributeSet 方法</span><span class="sxs-lookup"><span data-stu-id="31f54-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="31f54-103">建立一組安全性許可權，以附加至指定之標記所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="31f54-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f54-104">語法</span><span class="sxs-lookup"><span data-stu-id="31f54-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31f54-105">參數</span><span class="sxs-lookup"><span data-stu-id="31f54-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="31f54-106">在安全性資訊所附加的 token。</span><span class="sxs-lookup"><span data-stu-id="31f54-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="31f54-107">在結構的陣列 `COR_SECATTR` 。</span><span class="sxs-lookup"><span data-stu-id="31f54-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="31f54-108">在中的元素數目 `rSecAttrs` 。</span><span class="sxs-lookup"><span data-stu-id="31f54-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="31f54-109">脫銷如果方法失敗，會在導致問題的元素中指定索引 `rSecAttrs` 。</span><span class="sxs-lookup"><span data-stu-id="31f54-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f54-110">需求</span><span class="sxs-lookup"><span data-stu-id="31f54-110">Requirements</span></span>  
 <span data-ttu-id="31f54-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31f54-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f54-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="31f54-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31f54-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="31f54-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31f54-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31f54-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f54-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31f54-115">See also</span></span>

- [<span data-ttu-id="31f54-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="31f54-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="31f54-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="31f54-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
