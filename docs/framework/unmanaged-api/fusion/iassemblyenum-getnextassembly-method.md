---
title: "IAssemblyEnum::GetNextAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyEnum.GetNextAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cef1624d0432d571edfddfa772f31366e23074f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="fc85f-102">IAssemblyEnum::GetNextAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="fc85f-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="fc85f-103">取得下一個指標[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)包含在這個[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="fc85f-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc85f-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc85f-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc85f-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc85f-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="fc85f-106">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="fc85f-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="fc85f-107">`pvReserved`必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="fc85f-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="fc85f-108">[out]傳回`IAssemblyName`指標。</span><span class="sxs-lookup"><span data-stu-id="fc85f-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fc85f-109">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="fc85f-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="fc85f-110">`dwFlags`必須是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="fc85f-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc85f-111">需求</span><span class="sxs-lookup"><span data-stu-id="fc85f-111">Requirements</span></span>  
 <span data-ttu-id="fc85f-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc85f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc85f-113">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="fc85f-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fc85f-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc85f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc85f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc85f-115">See Also</span></span>  
 [<span data-ttu-id="fc85f-116">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="fc85f-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="fc85f-117">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="fc85f-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
