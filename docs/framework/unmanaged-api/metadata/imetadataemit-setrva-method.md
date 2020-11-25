---
title: IMetaDataEmit::SetRVA 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
ms.openlocfilehash: df9dc1a36a9adcef3f93a9929565cef117e84d75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704223"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="72c1d-102">IMetaDataEmit::SetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="72c1d-102">IMetaDataEmit::SetRVA Method</span></span>

<span data-ttu-id="72c1d-103">設定指定方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="72c1d-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72c1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="72c1d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72c1d-105">參數</span><span class="sxs-lookup"><span data-stu-id="72c1d-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="72c1d-106">在目標方法或方法執行的標記。</span><span class="sxs-lookup"><span data-stu-id="72c1d-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="72c1d-107">在程式碼或資料區域的位址。</span><span class="sxs-lookup"><span data-stu-id="72c1d-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72c1d-108">需求</span><span class="sxs-lookup"><span data-stu-id="72c1d-108">Requirements</span></span>  

 <span data-ttu-id="72c1d-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72c1d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72c1d-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="72c1d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72c1d-111">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="72c1d-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72c1d-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72c1d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c1d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72c1d-113">See also</span></span>

- [<span data-ttu-id="72c1d-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="72c1d-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="72c1d-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="72c1d-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
