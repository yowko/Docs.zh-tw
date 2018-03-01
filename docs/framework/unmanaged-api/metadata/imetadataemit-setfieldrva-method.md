---
title: "IMetaDataEmit::SetFieldRVA 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 260d5458af9fb8fbc8161018c438346fd58af06f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="9e74b-102">IMetaDataEmit::SetFieldRVA 方法</span><span class="sxs-lookup"><span data-stu-id="9e74b-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="9e74b-103">設定指定的語彙基元所參考之欄位的相對虛擬位址的全域變數值。</span><span class="sxs-lookup"><span data-stu-id="9e74b-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e74b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e74b-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e74b-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e74b-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="9e74b-106">[in]目標欄位語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9e74b-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="9e74b-107">[in]程式碼或資料區的位址。</span><span class="sxs-lookup"><span data-stu-id="9e74b-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e74b-108">需求</span><span class="sxs-lookup"><span data-stu-id="9e74b-108">Requirements</span></span>  
 <span data-ttu-id="9e74b-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e74b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e74b-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9e74b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e74b-111">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9e74b-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e74b-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e74b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e74b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e74b-113">See Also</span></span>  
 [<span data-ttu-id="9e74b-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9e74b-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9e74b-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="9e74b-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
