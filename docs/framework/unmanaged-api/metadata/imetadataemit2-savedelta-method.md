---
title: IMetaDataEmit2::SaveDelta 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7098bceee6bf60cd7781606ffc889b6af9c3e3cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445331"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="5942f-102">IMetaDataEmit2::SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="5942f-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="5942f-103">將目前的編輯後繼續工作階段的變更儲存至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="5942f-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5942f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5942f-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5942f-105">參數</span><span class="sxs-lookup"><span data-stu-id="5942f-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="5942f-106">[in]變更用來儲存的檔名。</span><span class="sxs-lookup"><span data-stu-id="5942f-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="5942f-107">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="5942f-107">[in] Reserved.</span></span> <span data-ttu-id="5942f-108">必須是零。</span><span class="sxs-lookup"><span data-stu-id="5942f-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5942f-109">需求</span><span class="sxs-lookup"><span data-stu-id="5942f-109">Requirements</span></span>  
 <span data-ttu-id="5942f-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5942f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5942f-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5942f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5942f-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5942f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5942f-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5942f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5942f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5942f-114">See Also</span></span>  
 [<span data-ttu-id="5942f-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="5942f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="5942f-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5942f-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
