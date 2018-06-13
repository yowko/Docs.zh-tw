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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71881fe8c4b883bb91468033a3c17c8d77c35f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445418"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="147c5-102">IMetaDataEmit::SetMethodImplFlags 方法</span><span class="sxs-lookup"><span data-stu-id="147c5-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="147c5-103">設定或更新繼承的方法實作中所指定的語彙基元所參考的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="147c5-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="147c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="147c5-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="147c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="147c5-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="147c5-106">[in]若要變更方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="147c5-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="147c5-107">[in]值的組合[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉，指定方法實作功能。</span><span class="sxs-lookup"><span data-stu-id="147c5-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="147c5-108">需求</span><span class="sxs-lookup"><span data-stu-id="147c5-108">Requirements</span></span>  
 <span data-ttu-id="147c5-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="147c5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="147c5-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="147c5-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="147c5-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="147c5-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="147c5-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="147c5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147c5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="147c5-113">See Also</span></span>  
 [<span data-ttu-id="147c5-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="147c5-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="147c5-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="147c5-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
