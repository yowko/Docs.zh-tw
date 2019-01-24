---
title: IMetaDataError 介面
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe2f683ae46d1ee6205f97536976a358e86fc53d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720375"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="b261b-102">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="b261b-102">IMetaDataError Interface</span></span>
<span data-ttu-id="b261b-103">提供回呼機制，中繼資料合併期間回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="b261b-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b261b-104">`IMetaDataError`介面必須由用戶端實作。</span><span class="sxs-lookup"><span data-stu-id="b261b-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b261b-105">方法</span><span class="sxs-lookup"><span data-stu-id="b261b-105">Methods</span></span>  
  
|<span data-ttu-id="b261b-106">方法</span><span class="sxs-lookup"><span data-stu-id="b261b-106">Method</span></span>|<span data-ttu-id="b261b-107">描述</span><span class="sxs-lookup"><span data-stu-id="b261b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b261b-108">OnError 方法</span><span class="sxs-lookup"><span data-stu-id="b261b-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="b261b-109">提供中繼資料合併期間所發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="b261b-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b261b-110">需求</span><span class="sxs-lookup"><span data-stu-id="b261b-110">Requirements</span></span>  
 <span data-ttu-id="b261b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b261b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b261b-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b261b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b261b-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b261b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b261b-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b261b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b261b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b261b-115">See also</span></span>
- [<span data-ttu-id="b261b-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="b261b-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
