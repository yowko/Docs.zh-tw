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
ms.openlocfilehash: dad916d74c4e754d8fd3ffb62024e49617f5de05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702013"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="ff827-102">IMetaDataEmit2::SaveDeltaToStream 方法</span><span class="sxs-lookup"><span data-stu-id="ff827-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>

<span data-ttu-id="ff827-103">將目前的編輯後繼續會話的變更儲存至指定的資料流程。</span><span class="sxs-lookup"><span data-stu-id="ff827-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff827-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff827-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff827-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff827-105">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="ff827-106">在要儲存變更之可寫入資料流程的介面指標。</span><span class="sxs-lookup"><span data-stu-id="ff827-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="ff827-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="ff827-107">[in] Reserved.</span></span> <span data-ttu-id="ff827-108">這個值必須為零。</span><span class="sxs-lookup"><span data-stu-id="ff827-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff827-109">需求</span><span class="sxs-lookup"><span data-stu-id="ff827-109">Requirements</span></span>  

 <span data-ttu-id="ff827-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff827-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff827-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ff827-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff827-112">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ff827-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff827-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff827-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff827-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff827-114">See also</span></span>

- [<span data-ttu-id="ff827-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ff827-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="ff827-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ff827-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
