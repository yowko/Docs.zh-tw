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
ms.openlocfilehash: fadd1974cd4fa8a51a06700835f46df24e37d7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175768"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="de29b-102">IMetaDataEmit::DefineSecurityAttributeSet 方法</span><span class="sxs-lookup"><span data-stu-id="de29b-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="de29b-103">創建一組安全許可權以附加到指定權杖引用的物件。</span><span class="sxs-lookup"><span data-stu-id="de29b-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de29b-104">語法</span><span class="sxs-lookup"><span data-stu-id="de29b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de29b-105">參數</span><span class="sxs-lookup"><span data-stu-id="de29b-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="de29b-106">[在]附加安全資訊的權杖。</span><span class="sxs-lookup"><span data-stu-id="de29b-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="de29b-107">[在]結構陣列`COR_SECATTR`。</span><span class="sxs-lookup"><span data-stu-id="de29b-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="de29b-108">[在]中`rSecAttrs`的元素數。</span><span class="sxs-lookup"><span data-stu-id="de29b-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="de29b-109">[出]如果方法失敗，則指定導致問題的元素`rSecAttrs`中的索引。</span><span class="sxs-lookup"><span data-stu-id="de29b-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de29b-110">需求</span><span class="sxs-lookup"><span data-stu-id="de29b-110">Requirements</span></span>  
 <span data-ttu-id="de29b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de29b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de29b-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="de29b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de29b-113">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="de29b-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de29b-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de29b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de29b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de29b-115">See also</span></span>

- [<span data-ttu-id="de29b-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="de29b-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="de29b-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="de29b-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
