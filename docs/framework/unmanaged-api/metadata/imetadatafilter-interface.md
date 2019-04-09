---
title: IMetaDataFilter 介面
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4196ff2cb2d4ebc401076f603a8a7fdc9b9c76ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143789"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="3bb1b-102">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="3bb1b-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="3bb1b-103">提供標記和篩選中繼資料語彙基元的方法，以避免重複已採取的動作。</span><span class="sxs-lookup"><span data-stu-id="3bb1b-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3bb1b-104">方法</span><span class="sxs-lookup"><span data-stu-id="3bb1b-104">Methods</span></span>  
  
|<span data-ttu-id="3bb1b-105">方法</span><span class="sxs-lookup"><span data-stu-id="3bb1b-105">Method</span></span>|<span data-ttu-id="3bb1b-106">描述</span><span class="sxs-lookup"><span data-stu-id="3bb1b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3bb1b-107">IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="3bb1b-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="3bb1b-108">取得值，指出是否已經處理指定的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3bb1b-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="3bb1b-109">MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="3bb1b-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="3bb1b-110">設定值，指出指定的中繼資料語彙基元已處理。</span><span class="sxs-lookup"><span data-stu-id="3bb1b-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="3bb1b-111">UnmarkAll 方法</span><span class="sxs-lookup"><span data-stu-id="3bb1b-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="3bb1b-112">處理標記移除目前的中繼資料範圍內的所有權杖。</span><span class="sxs-lookup"><span data-stu-id="3bb1b-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bb1b-113">需求</span><span class="sxs-lookup"><span data-stu-id="3bb1b-113">Requirements</span></span>  
 <span data-ttu-id="3bb1b-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb1b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bb1b-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3bb1b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3bb1b-116">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3bb1b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3bb1b-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3bb1b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3bb1b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb1b-118">See also</span></span>

- [<span data-ttu-id="3bb1b-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="3bb1b-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
