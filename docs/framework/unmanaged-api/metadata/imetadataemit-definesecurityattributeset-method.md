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
ms.openlocfilehash: b98fab6c6127c3f78151d3b84160d4ca0434b6cd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428241"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="b4a23-102">IMetaDataEmit::DefineSecurityAttributeSet 方法</span><span class="sxs-lookup"><span data-stu-id="b4a23-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="b4a23-103">建立一組安全性許可權，以附加至指定之標記所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="b4a23-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a23-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4a23-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4a23-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4a23-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="b4a23-106">在安全性資訊所附加的 token。</span><span class="sxs-lookup"><span data-stu-id="b4a23-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="b4a23-107">在`COR_SECATTR` 結構的陣列。</span><span class="sxs-lookup"><span data-stu-id="b4a23-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="b4a23-108">在`rSecAttrs`中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="b4a23-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="b4a23-109">脫銷如果方法失敗，會在導致問題的元素 `rSecAttrs` 中指定索引。</span><span class="sxs-lookup"><span data-stu-id="b4a23-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4a23-110">需求</span><span class="sxs-lookup"><span data-stu-id="b4a23-110">Requirements</span></span>  
 <span data-ttu-id="b4a23-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4a23-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4a23-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b4a23-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b4a23-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="b4a23-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4a23-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4a23-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a23-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4a23-115">See also</span></span>

- [<span data-ttu-id="b4a23-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b4a23-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b4a23-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b4a23-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
