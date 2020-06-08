---
title: IMetaDataFilter::MarkToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: 28a5f79f6fa8d25fd254c4093b0f76e0308edbad
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492521"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="8ccf2-102">IMetaDataFilter::MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="8ccf2-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="8ccf2-103">設定值，指出已處理指定的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="8ccf2-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ccf2-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ccf2-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ccf2-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ccf2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="8ccf2-106">在要標示為已處理的標記。</span><span class="sxs-lookup"><span data-stu-id="8ccf2-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ccf2-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="8ccf2-107">Requirements</span></span>  
 <span data-ttu-id="8ccf2-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ccf2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ccf2-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8ccf2-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ccf2-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="8ccf2-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ccf2-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ccf2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccf2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ccf2-112">See also</span></span>

- [<span data-ttu-id="8ccf2-113">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="8ccf2-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
