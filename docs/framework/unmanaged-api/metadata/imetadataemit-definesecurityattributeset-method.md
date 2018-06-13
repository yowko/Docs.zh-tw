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
ms.openlocfilehash: 60cb1640d374ce71d1d2fb51ba536b53ddd39b92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443521"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="1cb41-102">IMetaDataEmit::DefineSecurityAttributeSet 方法</span><span class="sxs-lookup"><span data-stu-id="1cb41-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="1cb41-103">建立一組安全性權限，將附加到指定的語彙基元所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="1cb41-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cb41-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cb41-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cb41-105">參數</span><span class="sxs-lookup"><span data-stu-id="1cb41-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="1cb41-106">[in]要附加的安全性資訊的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1cb41-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="1cb41-107">[in]陣列`COR_SECATTR`結構。</span><span class="sxs-lookup"><span data-stu-id="1cb41-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="1cb41-108">[in]中的項目數`rSecAttrs`。</span><span class="sxs-lookup"><span data-stu-id="1cb41-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="1cb41-109">[out]如果方法失敗，會指定在索引`rSecAttrs`造成問題的項目。</span><span class="sxs-lookup"><span data-stu-id="1cb41-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cb41-110">需求</span><span class="sxs-lookup"><span data-stu-id="1cb41-110">Requirements</span></span>  
 <span data-ttu-id="1cb41-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb41-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cb41-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1cb41-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1cb41-113">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1cb41-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cb41-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cb41-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb41-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cb41-115">See Also</span></span>  
 [<span data-ttu-id="1cb41-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1cb41-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="1cb41-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1cb41-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
