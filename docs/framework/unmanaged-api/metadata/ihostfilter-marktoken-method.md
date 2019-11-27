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
ms.openlocfilehash: 6f8df824ed36b7793d5f07e5b5cf51f65f9c8e24
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432235"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="08711-102">IHostFilter::MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="08711-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="08711-103">表示將會處理指定的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="08711-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08711-104">語法</span><span class="sxs-lookup"><span data-stu-id="08711-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08711-105">參數</span><span class="sxs-lookup"><span data-stu-id="08711-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="08711-106">在要處理的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="08711-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08711-107">備註</span><span class="sxs-lookup"><span data-stu-id="08711-107">Remarks</span></span>  
 <span data-ttu-id="08711-108">一般而言，您想要在中繼資料範圍內處理權杖。</span><span class="sxs-lookup"><span data-stu-id="08711-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="08711-109">`MarkToken` 方法會透過[IMetaDataEmit：： SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)方法傳遞至中繼資料引擎。</span><span class="sxs-lookup"><span data-stu-id="08711-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08711-110">需求</span><span class="sxs-lookup"><span data-stu-id="08711-110">Requirements</span></span>  
 <span data-ttu-id="08711-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08711-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08711-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="08711-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08711-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="08711-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08711-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08711-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08711-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08711-115">See also</span></span>

- [<span data-ttu-id="08711-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="08711-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="08711-117">IHostFilter 介面</span><span class="sxs-lookup"><span data-stu-id="08711-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
