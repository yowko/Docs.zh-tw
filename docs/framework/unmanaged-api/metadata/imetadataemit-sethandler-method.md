---
title: IMetaDataEmit::SetHandler 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ada84df2a08b992aa178c2fb63c713b05a8937a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503212"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="153c1-102">IMetaDataEmit::SetHandler 方法</span><span class="sxs-lookup"><span data-stu-id="153c1-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="153c1-103">設定所指定參考的方法`IUnknown`指標當做權杖的重新對應的通知回呼。</span><span class="sxs-lookup"><span data-stu-id="153c1-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="153c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="153c1-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="153c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="153c1-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="153c1-106">[in]若要註冊處理常式。</span><span class="sxs-lookup"><span data-stu-id="153c1-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="153c1-107">備註</span><span class="sxs-lookup"><span data-stu-id="153c1-107">Remarks</span></span>  
 <span data-ttu-id="153c1-108">中繼資料引擎會使用所提供的方法來傳送通知`SetHandler`，到編譯器，並不會記錄產生最佳化的方式，而且，想要最佳化已儲存的記錄。</span><span class="sxs-lookup"><span data-stu-id="153c1-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="153c1-109">如果未透過來提供回呼方法，則`SetHandler`，將會執行任何最佳化上儲存除了其中數個匯入範圍已合併使用`IMapToken`合併每個領域。</span><span class="sxs-lookup"><span data-stu-id="153c1-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="153c1-110">需求</span><span class="sxs-lookup"><span data-stu-id="153c1-110">Requirements</span></span>  
 <span data-ttu-id="153c1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="153c1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="153c1-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="153c1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="153c1-113">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="153c1-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="153c1-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="153c1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="153c1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="153c1-115">See also</span></span>
- [<span data-ttu-id="153c1-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="153c1-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="153c1-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="153c1-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
