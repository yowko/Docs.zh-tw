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
ms.openlocfilehash: 7e8376f3a029b0e3ec51a1e7587dd14b3e7530ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177418"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="0d505-102">IMetaDataEmit2::SaveDeltaToStream 方法</span><span class="sxs-lookup"><span data-stu-id="0d505-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="0d505-103">將更改從當前編輯和繼續會話保存到指定的流。</span><span class="sxs-lookup"><span data-stu-id="0d505-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d505-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d505-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d505-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d505-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="0d505-106">[在]指向要保存到的可寫流的介面指標。</span><span class="sxs-lookup"><span data-stu-id="0d505-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="0d505-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="0d505-107">[in] Reserved.</span></span> <span data-ttu-id="0d505-108">這個值必須為零。</span><span class="sxs-lookup"><span data-stu-id="0d505-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d505-109">需求</span><span class="sxs-lookup"><span data-stu-id="0d505-109">Requirements</span></span>  
 <span data-ttu-id="0d505-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d505-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d505-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="0d505-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d505-112">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0d505-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d505-113">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d505-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d505-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d505-114">See also</span></span>

- [<span data-ttu-id="0d505-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="0d505-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="0d505-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0d505-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
