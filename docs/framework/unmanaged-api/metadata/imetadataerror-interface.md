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
ms.openlocfilehash: 5f5e04787ce0ab0e1c8ecf3c19ba37e76ba38bfe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701922"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="fbca0-102">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="fbca0-102">IMetaDataError Interface</span></span>

<span data-ttu-id="fbca0-103">提供回呼機制，用於報告中繼資料合併期間的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fbca0-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbca0-104">`IMetaDataError`介面必須由用戶端所執行。</span><span class="sxs-lookup"><span data-stu-id="fbca0-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fbca0-105">方法</span><span class="sxs-lookup"><span data-stu-id="fbca0-105">Methods</span></span>  
  
|<span data-ttu-id="fbca0-106">方法</span><span class="sxs-lookup"><span data-stu-id="fbca0-106">Method</span></span>|<span data-ttu-id="fbca0-107">描述</span><span class="sxs-lookup"><span data-stu-id="fbca0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fbca0-108">OnError 方法</span><span class="sxs-lookup"><span data-stu-id="fbca0-108">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="fbca0-109">提供在中繼資料合併期間發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="fbca0-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbca0-110">需求</span><span class="sxs-lookup"><span data-stu-id="fbca0-110">Requirements</span></span>  

 <span data-ttu-id="fbca0-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbca0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbca0-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="fbca0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbca0-113">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="fbca0-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fbca0-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbca0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbca0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbca0-115">See also</span></span>

- [<span data-ttu-id="fbca0-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="fbca0-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
