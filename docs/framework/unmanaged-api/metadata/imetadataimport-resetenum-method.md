---
title: "IMetaDataImport::ResetEnum 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResetEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2cdb4c00185d152be856a99e1fec9392fd2a4029
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="7fde2-102">IMetaDataImport::ResetEnum 方法</span><span class="sxs-lookup"><span data-stu-id="7fde2-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="7fde2-103">重設指定列舉程式至指定位置。</span><span class="sxs-lookup"><span data-stu-id="7fde2-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fde2-104">語法</span><span class="sxs-lookup"><span data-stu-id="7fde2-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7fde2-105">參數</span><span class="sxs-lookup"><span data-stu-id="7fde2-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="7fde2-106">[in]若要重設列舉值。</span><span class="sxs-lookup"><span data-stu-id="7fde2-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="7fde2-107">[in]在要放置列舉值的新位置。</span><span class="sxs-lookup"><span data-stu-id="7fde2-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fde2-108">需求</span><span class="sxs-lookup"><span data-stu-id="7fde2-108">Requirements</span></span>  
 <span data-ttu-id="7fde2-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7fde2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fde2-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7fde2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7fde2-111">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7fde2-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7fde2-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fde2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fde2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fde2-113">See Also</span></span>  
 [<span data-ttu-id="7fde2-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7fde2-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7fde2-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="7fde2-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
