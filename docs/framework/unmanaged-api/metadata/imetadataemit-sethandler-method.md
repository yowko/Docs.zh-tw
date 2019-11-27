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
ms.openlocfilehash: 6737275fb77e6f177832eb1d96214c37942bcd22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442163"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="1bb76-102">IMetaDataEmit::SetHandler 方法</span><span class="sxs-lookup"><span data-stu-id="1bb76-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="1bb76-103">將指定之 `IUnknown` 指標所參考的方法設定為權杖重新對應的通知回呼。</span><span class="sxs-lookup"><span data-stu-id="1bb76-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bb76-104">語法</span><span class="sxs-lookup"><span data-stu-id="1bb76-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bb76-105">參數</span><span class="sxs-lookup"><span data-stu-id="1bb76-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="1bb76-106">在要註冊的處理常式。</span><span class="sxs-lookup"><span data-stu-id="1bb76-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bb76-107">備註</span><span class="sxs-lookup"><span data-stu-id="1bb76-107">Remarks</span></span>  
 <span data-ttu-id="1bb76-108">中繼資料引擎會使用 `SetHandler`所提供的方法，將通知傳送給不會以優化方式產生記錄，而且想要將儲存的記錄優化的編譯器。</span><span class="sxs-lookup"><span data-stu-id="1bb76-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="1bb76-109">如果未透過 `SetHandler`提供回呼方法，則不會在儲存時執行優化，除非已使用每個範圍的 merge `IMapToken` 合併數個匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="1bb76-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bb76-110">需求</span><span class="sxs-lookup"><span data-stu-id="1bb76-110">Requirements</span></span>  
 <span data-ttu-id="1bb76-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb76-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bb76-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1bb76-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1bb76-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1bb76-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bb76-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bb76-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb76-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bb76-115">See also</span></span>

- [<span data-ttu-id="1bb76-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1bb76-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1bb76-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1bb76-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
