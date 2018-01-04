---
title: "IMetaDataEmit::SetMethodProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetMethodProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28ec0ba45a83ccf51cc84ee9deb2c658b9b106bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="f83c0-102">IMetaDataEmit::SetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="f83c0-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="f83c0-103">設定或更新功能，並儲存在指定相對虛擬位址，在先前呼叫所定義的方法[imetadataemit:: Definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f83c0-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f83c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="f83c0-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f83c0-105">參數</span><span class="sxs-lookup"><span data-stu-id="f83c0-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f83c0-106">[in]若要變更方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f83c0-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="f83c0-107">[in]成員屬性。</span><span class="sxs-lookup"><span data-stu-id="f83c0-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="f83c0-108">[in]程式碼的位址。</span><span class="sxs-lookup"><span data-stu-id="f83c0-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="f83c0-109">[in]方法的實作旗標。</span><span class="sxs-lookup"><span data-stu-id="f83c0-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f83c0-110">需求</span><span class="sxs-lookup"><span data-stu-id="f83c0-110">Requirements</span></span>  
 <span data-ttu-id="f83c0-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f83c0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f83c0-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f83c0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f83c0-113">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f83c0-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f83c0-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f83c0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83c0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="f83c0-115">See Also</span></span>  
 [<span data-ttu-id="f83c0-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f83c0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f83c0-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="f83c0-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
