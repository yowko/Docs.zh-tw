---
title: IMetaDataEmit::SetMethodImplFlags 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: 7ed7770f26ea4620d79f3be3f67e72f73c75057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175625"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="e8487-102">IMetaDataEmit::SetMethodImplFlags 方法</span><span class="sxs-lookup"><span data-stu-id="e8487-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="e8487-103">設置或更新指定權杖引用的繼承方法實現的中繼資料簽名。</span><span class="sxs-lookup"><span data-stu-id="e8487-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8487-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8487-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8487-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8487-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="e8487-106">[在]要更改的方法的權杖。</span><span class="sxs-lookup"><span data-stu-id="e8487-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="e8487-107">[在][CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)枚舉的值的組合，用於指定方法實現要素。</span><span class="sxs-lookup"><span data-stu-id="e8487-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8487-108">需求</span><span class="sxs-lookup"><span data-stu-id="e8487-108">Requirements</span></span>  
 <span data-ttu-id="e8487-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8487-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8487-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="e8487-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8487-111">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e8487-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8487-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8487-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8487-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8487-113">See also</span></span>

- [<span data-ttu-id="e8487-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="e8487-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e8487-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="e8487-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
