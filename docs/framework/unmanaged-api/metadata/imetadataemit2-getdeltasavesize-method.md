---
title: "IMetaDataEmit2::GetDeltaSaveSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.GetDeltaSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0a1b3aec06d6593257c82d6e3c08d6a8e2430691
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="a0c6b-102">IMetaDataEmit2::GetDeltaSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="a0c6b-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="a0c6b-103">取得值，指出目前的編輯後繼續工作階段產生的中繼資料大小的任何變更。</span><span class="sxs-lookup"><span data-stu-id="a0c6b-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0c6b-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0c6b-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0c6b-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="a0c6b-106">[in]其中一個[CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)值，表示所需的有效位數層級。</span><span class="sxs-lookup"><span data-stu-id="a0c6b-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="a0c6b-107">適用於.NET Framework 2.0 版中，這個參數已忽略。</span><span class="sxs-lookup"><span data-stu-id="a0c6b-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="a0c6b-108">[out]中繼資料的大小變化。</span><span class="sxs-lookup"><span data-stu-id="a0c6b-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0c6b-109">需求</span><span class="sxs-lookup"><span data-stu-id="a0c6b-109">Requirements</span></span>  
 <span data-ttu-id="a0c6b-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0c6b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0c6b-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0c6b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0c6b-112">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a0c6b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0c6b-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0c6b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c6b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c6b-114">See Also</span></span>  
 [<span data-ttu-id="a0c6b-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a0c6b-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="a0c6b-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a0c6b-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
