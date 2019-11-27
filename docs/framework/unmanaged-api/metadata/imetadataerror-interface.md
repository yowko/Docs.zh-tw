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
ms.openlocfilehash: 44ecb73375f8a408fb0a38c3a2e2913f92ec4ca4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441627"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="3e9aa-102">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="3e9aa-102">IMetaDataError Interface</span></span>
<span data-ttu-id="3e9aa-103">提供回呼機制，用於報告中繼資料合併期間的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3e9aa-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e9aa-104">`IMetaDataError` 介面必須由用戶端執行。</span><span class="sxs-lookup"><span data-stu-id="3e9aa-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e9aa-105">方法</span><span class="sxs-lookup"><span data-stu-id="3e9aa-105">Methods</span></span>  
  
|<span data-ttu-id="3e9aa-106">方法</span><span class="sxs-lookup"><span data-stu-id="3e9aa-106">Method</span></span>|<span data-ttu-id="3e9aa-107">描述</span><span class="sxs-lookup"><span data-stu-id="3e9aa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e9aa-108">OnError 方法</span><span class="sxs-lookup"><span data-stu-id="3e9aa-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="3e9aa-109">提供中繼資料合併期間發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="3e9aa-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e9aa-110">需求</span><span class="sxs-lookup"><span data-stu-id="3e9aa-110">Requirements</span></span>  
 <span data-ttu-id="3e9aa-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9aa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e9aa-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3e9aa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e9aa-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3e9aa-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e9aa-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e9aa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9aa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e9aa-115">See also</span></span>

- [<span data-ttu-id="3e9aa-116">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="3e9aa-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
