---
title: "IMetaDataEmit::ApplyEditAndContinue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.ApplyEditAndContinue
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d7744051bca9aeec677803f8b6c0bbbd0cdd1fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="8d427-102">IMetaDataEmit::ApplyEditAndContinue 方法</span><span class="sxs-lookup"><span data-stu-id="8d427-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="8d427-103">使用指定的中繼資料中所做的變更，更新目前組件範圍。</span><span class="sxs-lookup"><span data-stu-id="8d427-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d427-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d427-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d427-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d427-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="8d427-106">[in]指向 <<!--zzxref:IUnknown --> `IUnknown`> 表示可攜式執行檔 (PE) 檔案的差異中繼資料物件。</span><span class="sxs-lookup"><span data-stu-id="8d427-106">[in] Pointer to an <<!--zzxref:IUnknown --> `IUnknown`> object that represents the delta metadata from the portable executable (PE) file.</span></span>  
  
 <span data-ttu-id="8d427-107">差異中繼資料是包含此模組實際的中繼資料的複本所做的變更的中繼資料的區塊。</span><span class="sxs-lookup"><span data-stu-id="8d427-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d427-108">需求</span><span class="sxs-lookup"><span data-stu-id="8d427-108">Requirements</span></span>  
 <span data-ttu-id="8d427-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d427-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d427-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8d427-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d427-111">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d427-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d427-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d427-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d427-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d427-113">See Also</span></span>  
 [<span data-ttu-id="8d427-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="8d427-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8d427-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="8d427-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
