---
title: "IMetaDataEmit::SetHandler 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetHandler
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4a56db43f932a155b4251f019e39dc5640eb014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="c253a-102">IMetaDataEmit::SetHandler 方法</span><span class="sxs-lookup"><span data-stu-id="c253a-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="c253a-103">設定所指定參考的方法`IUnknown`指標當做權杖的重新對應的通知回呼。</span><span class="sxs-lookup"><span data-stu-id="c253a-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c253a-104">語法</span><span class="sxs-lookup"><span data-stu-id="c253a-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c253a-105">參數</span><span class="sxs-lookup"><span data-stu-id="c253a-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="c253a-106">[in]若要註冊處理常式。</span><span class="sxs-lookup"><span data-stu-id="c253a-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c253a-107">備註</span><span class="sxs-lookup"><span data-stu-id="c253a-107">Remarks</span></span>  
 <span data-ttu-id="c253a-108">中繼資料引擎會使用所提供的方法來傳送通知`SetHandler`，編譯器，並不會記錄產生以最佳化方式，並想要最佳化儲存的記錄。</span><span class="sxs-lookup"><span data-stu-id="c253a-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="c253a-109">如果未透過來提供回呼方法，則`SetHandler`，將會執行任何最佳化上儲存除了其中數個匯入範圍已經合併使用`IMapToken`合併的每個範圍。</span><span class="sxs-lookup"><span data-stu-id="c253a-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c253a-110">需求</span><span class="sxs-lookup"><span data-stu-id="c253a-110">Requirements</span></span>  
 <span data-ttu-id="c253a-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c253a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c253a-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c253a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c253a-113">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c253a-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c253a-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c253a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c253a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c253a-115">See Also</span></span>  
 [<span data-ttu-id="c253a-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c253a-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c253a-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c253a-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
