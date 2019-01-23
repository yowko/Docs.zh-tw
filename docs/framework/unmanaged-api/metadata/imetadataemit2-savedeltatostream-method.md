---
title: IMetaDataEmit2::SaveDeltaToStream 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0702a7a58e6bd8c13254da5adce17c9adf6fa0cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569451"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="11a10-102">IMetaDataEmit2::SaveDeltaToStream 方法</span><span class="sxs-lookup"><span data-stu-id="11a10-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="11a10-103">將變更儲存從目前的編輯和繼續工作階段指定的資料流。</span><span class="sxs-lookup"><span data-stu-id="11a10-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a10-104">語法</span><span class="sxs-lookup"><span data-stu-id="11a10-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11a10-105">參數</span><span class="sxs-lookup"><span data-stu-id="11a10-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="11a10-106">[in]要儲存的變更可寫入的資料流介面指標。</span><span class="sxs-lookup"><span data-stu-id="11a10-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="11a10-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="11a10-107">[in] Reserved.</span></span> <span data-ttu-id="11a10-108">此值必須是零。</span><span class="sxs-lookup"><span data-stu-id="11a10-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a10-109">需求</span><span class="sxs-lookup"><span data-stu-id="11a10-109">Requirements</span></span>  
 <span data-ttu-id="11a10-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11a10-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a10-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11a10-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11a10-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11a10-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11a10-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a10-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a10-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11a10-114">See also</span></span>
- [<span data-ttu-id="11a10-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="11a10-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="11a10-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="11a10-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
