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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f244d256d3af104d1d0c65769e82a87d6de046e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043911"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="93de2-102">IMetaDataEmit::DefineSecurityAttributeSet 方法</span><span class="sxs-lookup"><span data-stu-id="93de2-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="93de2-103">建立一組安全性權限，將附加到指定的語彙基元所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="93de2-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93de2-104">語法</span><span class="sxs-lookup"><span data-stu-id="93de2-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93de2-105">參數</span><span class="sxs-lookup"><span data-stu-id="93de2-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="93de2-106">[in]要附加的安全性資訊之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="93de2-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="93de2-107">[in]陣列`COR_SECATTR`結構。</span><span class="sxs-lookup"><span data-stu-id="93de2-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="93de2-108">[in]中的項目數`rSecAttrs`。</span><span class="sxs-lookup"><span data-stu-id="93de2-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="93de2-109">[out]如果方法失敗，會指定在索引`rSecAttrs`造成該問題的項目。</span><span class="sxs-lookup"><span data-stu-id="93de2-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93de2-110">需求</span><span class="sxs-lookup"><span data-stu-id="93de2-110">Requirements</span></span>  
 <span data-ttu-id="93de2-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93de2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93de2-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="93de2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93de2-113">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="93de2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93de2-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93de2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93de2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93de2-115">See also</span></span>

- [<span data-ttu-id="93de2-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="93de2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="93de2-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="93de2-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
