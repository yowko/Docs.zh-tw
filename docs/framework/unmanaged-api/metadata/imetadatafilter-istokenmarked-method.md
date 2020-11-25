---
title: IMetaDataFilter::IsTokenMarked 方法
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
ms.openlocfilehash: ce7292003872805c9390ce3d9c59b39497a83ed1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701831"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="636c1-102">IMetaDataFilter::IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="636c1-102">IMetaDataFilter::IsTokenMarked Method</span></span>

<span data-ttu-id="636c1-103">取得值，這個值表示指定的元資料標記是否已標示為已處理。</span><span class="sxs-lookup"><span data-stu-id="636c1-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="636c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="636c1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="636c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="636c1-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="636c1-106">在要檢查處理標記的標記。</span><span class="sxs-lookup"><span data-stu-id="636c1-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="636c1-107">擴展 `true` 如果已處理，則為值， `tk` 否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="636c1-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="636c1-108">需求</span><span class="sxs-lookup"><span data-stu-id="636c1-108">Requirements</span></span>  

 <span data-ttu-id="636c1-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="636c1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="636c1-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="636c1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="636c1-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="636c1-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="636c1-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="636c1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="636c1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="636c1-113">See also</span></span>

- [<span data-ttu-id="636c1-114">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="636c1-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
