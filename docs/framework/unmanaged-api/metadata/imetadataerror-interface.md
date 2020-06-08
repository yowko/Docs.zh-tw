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
ms.openlocfilehash: 46370da4e61dc90f2386170745da4f95ac7de63b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492753"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="51f99-102">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="51f99-102">IMetaDataError Interface</span></span>
<span data-ttu-id="51f99-103">提供回呼機制，用於報告中繼資料合併期間的錯誤。</span><span class="sxs-lookup"><span data-stu-id="51f99-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51f99-104">`IMetaDataError`介面必須由用戶端執行。</span><span class="sxs-lookup"><span data-stu-id="51f99-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51f99-105">方法</span><span class="sxs-lookup"><span data-stu-id="51f99-105">Methods</span></span>  
  
|<span data-ttu-id="51f99-106">方法</span><span class="sxs-lookup"><span data-stu-id="51f99-106">Method</span></span>|<span data-ttu-id="51f99-107">描述</span><span class="sxs-lookup"><span data-stu-id="51f99-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51f99-108">OnError 方法</span><span class="sxs-lookup"><span data-stu-id="51f99-108">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="51f99-109">提供中繼資料合併期間發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="51f99-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51f99-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="51f99-110">Requirements</span></span>  
 <span data-ttu-id="51f99-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51f99-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51f99-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="51f99-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51f99-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="51f99-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51f99-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51f99-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f99-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f99-115">See also</span></span>

- [<span data-ttu-id="51f99-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="51f99-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
