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
ms.openlocfilehash: 9662a14b4ea97aed16968083489324d46c38dda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177516"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="3efdb-102">IMetaDataEmit::SetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="3efdb-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="3efdb-103">設置或更新由之前調用[IMetaDataEmit：:DefineMethod）](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)定義的方法的要素（存儲在指定的相對虛擬位址）</span><span class="sxs-lookup"><span data-stu-id="3efdb-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3efdb-104">語法</span><span class="sxs-lookup"><span data-stu-id="3efdb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3efdb-105">參數</span><span class="sxs-lookup"><span data-stu-id="3efdb-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="3efdb-106">[在]要更改的方法的權杖。</span><span class="sxs-lookup"><span data-stu-id="3efdb-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="3efdb-107">[在]成員屬性。</span><span class="sxs-lookup"><span data-stu-id="3efdb-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="3efdb-108">[在]代碼的位址。</span><span class="sxs-lookup"><span data-stu-id="3efdb-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="3efdb-109">[在]方法的實現標誌。</span><span class="sxs-lookup"><span data-stu-id="3efdb-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3efdb-110">需求</span><span class="sxs-lookup"><span data-stu-id="3efdb-110">Requirements</span></span>  
 <span data-ttu-id="3efdb-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3efdb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3efdb-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="3efdb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3efdb-113">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3efdb-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3efdb-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3efdb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3efdb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3efdb-115">See also</span></span>

- [<span data-ttu-id="3efdb-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3efdb-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3efdb-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="3efdb-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
