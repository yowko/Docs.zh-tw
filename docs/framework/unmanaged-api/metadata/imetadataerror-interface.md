---
title: "IMetaDataError 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataError
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataError
helpviewer_keywords: IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ae90221a1b305fdf09ae9583e720a2092289362
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="e5d98-102">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="e5d98-102">IMetaDataError Interface</span></span>
<span data-ttu-id="e5d98-103">提供回呼機制，以報告錯誤期間的中繼資料合併。</span><span class="sxs-lookup"><span data-stu-id="e5d98-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5d98-104">`IMetaDataError`介面必須由用戶端實作。</span><span class="sxs-lookup"><span data-stu-id="e5d98-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5d98-105">方法</span><span class="sxs-lookup"><span data-stu-id="e5d98-105">Methods</span></span>  
  
|<span data-ttu-id="e5d98-106">方法</span><span class="sxs-lookup"><span data-stu-id="e5d98-106">Method</span></span>|<span data-ttu-id="e5d98-107">說明</span><span class="sxs-lookup"><span data-stu-id="e5d98-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5d98-108">OnError 方法</span><span class="sxs-lookup"><span data-stu-id="e5d98-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="e5d98-109">提供中繼資料合併期間發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="e5d98-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5d98-110">需求</span><span class="sxs-lookup"><span data-stu-id="e5d98-110">Requirements</span></span>  
 <span data-ttu-id="e5d98-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5d98-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5d98-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5d98-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5d98-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e5d98-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5d98-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5d98-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d98-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5d98-115">See Also</span></span>  
 [<span data-ttu-id="e5d98-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="e5d98-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
