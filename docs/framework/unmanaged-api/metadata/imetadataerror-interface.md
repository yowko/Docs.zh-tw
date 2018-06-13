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
ms.openlocfilehash: 1c264bfd31f8cd31bacf2d194ddbd07338569294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447166"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="f59f5-102">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="f59f5-102">IMetaDataError Interface</span></span>
<span data-ttu-id="f59f5-103">提供回呼機制，以報告錯誤期間的中繼資料合併。</span><span class="sxs-lookup"><span data-stu-id="f59f5-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f59f5-104">`IMetaDataError`介面必須由用戶端實作。</span><span class="sxs-lookup"><span data-stu-id="f59f5-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f59f5-105">方法</span><span class="sxs-lookup"><span data-stu-id="f59f5-105">Methods</span></span>  
  
|<span data-ttu-id="f59f5-106">方法</span><span class="sxs-lookup"><span data-stu-id="f59f5-106">Method</span></span>|<span data-ttu-id="f59f5-107">描述</span><span class="sxs-lookup"><span data-stu-id="f59f5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f59f5-108">OnError 方法</span><span class="sxs-lookup"><span data-stu-id="f59f5-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="f59f5-109">提供中繼資料合併期間發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="f59f5-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f59f5-110">需求</span><span class="sxs-lookup"><span data-stu-id="f59f5-110">Requirements</span></span>  
 <span data-ttu-id="f59f5-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f59f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f59f5-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f59f5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f59f5-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f59f5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f59f5-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f59f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f59f5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f59f5-115">See Also</span></span>  
 [<span data-ttu-id="f59f5-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="f59f5-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
