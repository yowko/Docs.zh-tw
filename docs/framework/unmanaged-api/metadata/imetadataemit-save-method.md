---
title: "IMetaDataEmit::Save 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Save
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a11241894116f57889a15a184290cd95f2f4f54f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="140fd-102">IMetaDataEmit::Save 方法</span><span class="sxs-lookup"><span data-stu-id="140fd-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="140fd-103">在指定的位址的檔案目前範圍中儲存所有的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="140fd-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="140fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="140fd-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="140fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="140fd-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="140fd-106">[in]若要將儲存至檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="140fd-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="140fd-107">如果這個值是 null，記憶體中複本會儲存到最後一個使用的位置。</span><span class="sxs-lookup"><span data-stu-id="140fd-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="140fd-108">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="140fd-108">[in] Reserved.</span></span> <span data-ttu-id="140fd-109">必須是零。</span><span class="sxs-lookup"><span data-stu-id="140fd-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="140fd-110">需求</span><span class="sxs-lookup"><span data-stu-id="140fd-110">Requirements</span></span>  
 <span data-ttu-id="140fd-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="140fd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="140fd-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="140fd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="140fd-113">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="140fd-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="140fd-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="140fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="140fd-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="140fd-115">See Also</span></span>  
 [<span data-ttu-id="140fd-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="140fd-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="140fd-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="140fd-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
