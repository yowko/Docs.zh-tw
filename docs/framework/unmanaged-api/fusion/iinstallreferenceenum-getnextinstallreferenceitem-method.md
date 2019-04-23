---
title: IInstallReferenceEnum::GetNextInstallReferenceItem 方法
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc04bb12e4271a3237ebef140c481620fc01ad7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202374"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="2e260-102">IInstallReferenceEnum::GetNextInstallReferenceItem 方法</span><span class="sxs-lookup"><span data-stu-id="2e260-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="2e260-103">取得下一個指標[IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)中所包含的物件[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="2e260-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e260-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e260-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e260-105">參數</span><span class="sxs-lookup"><span data-stu-id="2e260-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="2e260-106">[out]傳回`IInstallReferenceItem`指標。</span><span class="sxs-lookup"><span data-stu-id="2e260-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2e260-107">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="2e260-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2e260-108">`dwFlags` 必須是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="2e260-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2e260-109">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="2e260-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2e260-110">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="2e260-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e260-111">需求</span><span class="sxs-lookup"><span data-stu-id="2e260-111">Requirements</span></span>  
 <span data-ttu-id="2e260-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2e260-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e260-113">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2e260-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2e260-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e260-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e260-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e260-115">See also</span></span>

- [<span data-ttu-id="2e260-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="2e260-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="2e260-117">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="2e260-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
