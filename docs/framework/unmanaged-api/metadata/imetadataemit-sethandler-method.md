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
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177534"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="71a4d-102">IMetaDataEmit::SetHandler 方法</span><span class="sxs-lookup"><span data-stu-id="71a4d-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="71a4d-103">將指定`IUnknown`指標引用的方法集為權杖重映射的通知回檔。</span><span class="sxs-lookup"><span data-stu-id="71a4d-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71a4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="71a4d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71a4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="71a4d-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="71a4d-106">[在]要註冊的處理常式。</span><span class="sxs-lookup"><span data-stu-id="71a4d-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71a4d-107">備註</span><span class="sxs-lookup"><span data-stu-id="71a4d-107">Remarks</span></span>  
 <span data-ttu-id="71a4d-108">中繼資料引擎使用 提供`SetHandler`的方法向未以優化方式生成記錄並希望優化保存的記錄的編譯器發送通知。</span><span class="sxs-lookup"><span data-stu-id="71a4d-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="71a4d-109">如果未通過`SetHandler`提供回檔方法，則不會對保存執行優化，除非每個作用域在合併`IMapToken`時合併了多個導入作用域。</span><span class="sxs-lookup"><span data-stu-id="71a4d-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71a4d-110">需求</span><span class="sxs-lookup"><span data-stu-id="71a4d-110">Requirements</span></span>  
 <span data-ttu-id="71a4d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71a4d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71a4d-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="71a4d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71a4d-113">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="71a4d-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71a4d-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71a4d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a4d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71a4d-115">See also</span></span>

- [<span data-ttu-id="71a4d-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="71a4d-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="71a4d-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="71a4d-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
