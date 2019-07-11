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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f486ffd1206dd30fa29d3f07c8c5b738cc207db0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745867"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="d8d1c-102">IHostFilter::MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="d8d1c-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="d8d1c-103">表示將處理指定的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d8d1c-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8d1c-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8d1c-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8d1c-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8d1c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d8d1c-106">[in]處理中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d8d1c-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8d1c-107">備註</span><span class="sxs-lookup"><span data-stu-id="d8d1c-107">Remarks</span></span>  
 <span data-ttu-id="d8d1c-108">一般而言，您會想在中繼資料範圍內無法處理的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d8d1c-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="d8d1c-109">`MarkToken`方法傳遞至中繼資料引擎，透過[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d8d1c-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8d1c-110">需求</span><span class="sxs-lookup"><span data-stu-id="d8d1c-110">Requirements</span></span>  
 <span data-ttu-id="d8d1c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8d1c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8d1c-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8d1c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8d1c-113">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d8d1c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8d1c-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8d1c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d1c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8d1c-115">See also</span></span>

- [<span data-ttu-id="d8d1c-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="d8d1c-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="d8d1c-117">IHostFilter 介面</span><span class="sxs-lookup"><span data-stu-id="d8d1c-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
