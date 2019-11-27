---
title: IMetaDataEmit::SaveToStream 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 23f6186b2561cbcd52db767616d986084f33860b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435924"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="77a3e-102">IMetaDataEmit::SaveToStream 方法</span><span class="sxs-lookup"><span data-stu-id="77a3e-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="77a3e-103">將目前範圍中的所有中繼資料儲存至指定的 `IStream`。</span><span class="sxs-lookup"><span data-stu-id="77a3e-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="77a3e-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77a3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="77a3e-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="77a3e-106">在要儲存的可寫入資料流程。</span><span class="sxs-lookup"><span data-stu-id="77a3e-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="77a3e-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="77a3e-107">[in] Reserved.</span></span> <span data-ttu-id="77a3e-108">必須為零。</span><span class="sxs-lookup"><span data-stu-id="77a3e-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77a3e-109">需求</span><span class="sxs-lookup"><span data-stu-id="77a3e-109">Requirements</span></span>  
 <span data-ttu-id="77a3e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77a3e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77a3e-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="77a3e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77a3e-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="77a3e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77a3e-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77a3e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a3e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77a3e-114">See also</span></span>

- [<span data-ttu-id="77a3e-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="77a3e-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="77a3e-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="77a3e-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
