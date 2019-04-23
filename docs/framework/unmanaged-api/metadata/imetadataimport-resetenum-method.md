---
title: IMetaDataImport::ResetEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 143b11f0a99081b7d49bfbb68b635d92cf1e9ba3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163874"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="e21a7-102">IMetaDataImport::ResetEnum 方法</span><span class="sxs-lookup"><span data-stu-id="e21a7-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="e21a7-103">重設指定列舉程式至指定位置。</span><span class="sxs-lookup"><span data-stu-id="e21a7-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e21a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e21a7-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e21a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e21a7-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e21a7-106">[in]若要重設列舉值。</span><span class="sxs-lookup"><span data-stu-id="e21a7-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="e21a7-107">[in]在要放置列舉值的新位置。</span><span class="sxs-lookup"><span data-stu-id="e21a7-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e21a7-108">需求</span><span class="sxs-lookup"><span data-stu-id="e21a7-108">Requirements</span></span>  
 <span data-ttu-id="e21a7-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e21a7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e21a7-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e21a7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e21a7-111">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e21a7-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e21a7-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e21a7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21a7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e21a7-113">See also</span></span>

- [<span data-ttu-id="e21a7-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e21a7-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e21a7-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e21a7-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
