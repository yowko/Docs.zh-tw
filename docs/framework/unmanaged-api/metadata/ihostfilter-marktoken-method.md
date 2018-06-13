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
ms.openlocfilehash: 52375486eb9d7780a51808dedc5f876587efb115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444560"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="a9399-102">IHostFilter::MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="a9399-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="a9399-103">表示將處理指定的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a9399-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9399-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9399-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9399-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9399-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a9399-106">[in]要處理的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a9399-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9399-107">備註</span><span class="sxs-lookup"><span data-stu-id="a9399-107">Remarks</span></span>  
 <span data-ttu-id="a9399-108">您通常會想要如果在中繼資料範圍內處理的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a9399-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="a9399-109">`MarkToken`方法傳遞至中繼資料引擎透過[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a9399-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9399-110">需求</span><span class="sxs-lookup"><span data-stu-id="a9399-110">Requirements</span></span>  
 <span data-ttu-id="a9399-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9399-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9399-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a9399-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9399-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a9399-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9399-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9399-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9399-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9399-115">See Also</span></span>  
 [<span data-ttu-id="a9399-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="a9399-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="a9399-117">IHostFilter 介面</span><span class="sxs-lookup"><span data-stu-id="a9399-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
