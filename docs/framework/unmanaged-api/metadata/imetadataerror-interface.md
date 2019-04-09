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
ms.openlocfilehash: 37f1f6055ec8fa68fe804780d2893d20c978e6bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188626"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="d539a-102">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="d539a-102">IMetaDataError Interface</span></span>
<span data-ttu-id="d539a-103">提供回呼機制，中繼資料合併期間回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="d539a-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d539a-104">`IMetaDataError`介面必須由用戶端實作。</span><span class="sxs-lookup"><span data-stu-id="d539a-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d539a-105">方法</span><span class="sxs-lookup"><span data-stu-id="d539a-105">Methods</span></span>  
  
|<span data-ttu-id="d539a-106">方法</span><span class="sxs-lookup"><span data-stu-id="d539a-106">Method</span></span>|<span data-ttu-id="d539a-107">描述</span><span class="sxs-lookup"><span data-stu-id="d539a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d539a-108">OnError 方法</span><span class="sxs-lookup"><span data-stu-id="d539a-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="d539a-109">提供中繼資料合併期間所發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="d539a-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d539a-110">需求</span><span class="sxs-lookup"><span data-stu-id="d539a-110">Requirements</span></span>  
 <span data-ttu-id="d539a-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d539a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d539a-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d539a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d539a-113">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d539a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d539a-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d539a-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d539a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d539a-115">See also</span></span>

- [<span data-ttu-id="d539a-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="d539a-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
