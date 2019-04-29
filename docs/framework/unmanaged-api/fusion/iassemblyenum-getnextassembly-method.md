---
title: IAssemblyEnum::GetNextAssembly 方法
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a77e468363b59e76e55aa24d97d064189ad297e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697468"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="8c87a-102">IAssemblyEnum::GetNextAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="8c87a-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="8c87a-103">取得下一個指標[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)包含在此[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="8c87a-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c87a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c87a-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c87a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c87a-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="8c87a-106">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="8c87a-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8c87a-107">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="8c87a-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="8c87a-108">[out]傳回`IAssemblyName`指標。</span><span class="sxs-lookup"><span data-stu-id="8c87a-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8c87a-109">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="8c87a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8c87a-110">`dwFlags` 必須是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="8c87a-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c87a-111">需求</span><span class="sxs-lookup"><span data-stu-id="8c87a-111">Requirements</span></span>  
 <span data-ttu-id="8c87a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c87a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c87a-113">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8c87a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8c87a-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c87a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c87a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c87a-115">See also</span></span>

- [<span data-ttu-id="8c87a-116">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="8c87a-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="8c87a-117">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8c87a-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
