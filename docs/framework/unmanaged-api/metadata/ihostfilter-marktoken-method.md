---
title: IHostFilter::MarkToken 方法
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
ms.openlocfilehash: 11529ce896f265f2b200fa6e511d4b913e9147c8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008218"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="6da33-102">IHostFilter::MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="6da33-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="6da33-103">表示將會處理指定的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="6da33-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6da33-104">語法</span><span class="sxs-lookup"><span data-stu-id="6da33-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6da33-105">參數</span><span class="sxs-lookup"><span data-stu-id="6da33-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6da33-106">在要處理的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="6da33-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6da33-107">備註</span><span class="sxs-lookup"><span data-stu-id="6da33-107">Remarks</span></span>  
 <span data-ttu-id="6da33-108">一般而言，您想要在中繼資料範圍內處理權杖。</span><span class="sxs-lookup"><span data-stu-id="6da33-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="6da33-109">`MarkToken`方法會透過[IMetaDataEmit：： SetHandler](imetadataemit-sethandler-method.md)方法傳遞至中繼資料引擎。</span><span class="sxs-lookup"><span data-stu-id="6da33-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6da33-110">需求</span><span class="sxs-lookup"><span data-stu-id="6da33-110">Requirements</span></span>  
 <span data-ttu-id="6da33-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6da33-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6da33-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6da33-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6da33-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6da33-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6da33-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6da33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6da33-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6da33-115">See also</span></span>

- [<span data-ttu-id="6da33-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="6da33-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="6da33-117">IHostFilter 介面</span><span class="sxs-lookup"><span data-stu-id="6da33-117">IHostFilter Interface</span></span>](ihostfilter-interface.md)
