---
title: IMetaDataEmit::SetMethodProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 534afdd5990435c6b4db5ef8ea27a8065b199496
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183595"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="861e0-102">IMetaDataEmit::SetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="861e0-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="861e0-103">設定或更新功能，並儲存在指定相對虛擬位址，定義由先前呼叫的方法[imetadataemit:: Definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="861e0-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="861e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="861e0-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="861e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="861e0-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="861e0-106">[in]若要變更方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="861e0-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="861e0-107">[in]成員屬性。</span><span class="sxs-lookup"><span data-stu-id="861e0-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="861e0-108">[in]程式碼的位址。</span><span class="sxs-lookup"><span data-stu-id="861e0-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="861e0-109">[in]方法的實作旗標。</span><span class="sxs-lookup"><span data-stu-id="861e0-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="861e0-110">需求</span><span class="sxs-lookup"><span data-stu-id="861e0-110">Requirements</span></span>  
 <span data-ttu-id="861e0-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="861e0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="861e0-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="861e0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="861e0-113">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="861e0-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="861e0-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="861e0-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="861e0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="861e0-115">See also</span></span>

- [<span data-ttu-id="861e0-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="861e0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="861e0-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="861e0-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
