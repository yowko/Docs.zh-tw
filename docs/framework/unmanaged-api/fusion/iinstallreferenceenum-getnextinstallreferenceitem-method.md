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
ms.openlocfilehash: 20e2bff4257df64f761fd8fff880643d4e786748
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796453"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="05902-102">IInstallReferenceEnum::GetNextInstallReferenceItem 方法</span><span class="sxs-lookup"><span data-stu-id="05902-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="05902-103">取得包含在這個[IInstallReferenceEnum](iinstallreferenceenum-interface.md)物件中的下一個[IInstallReferenceItem](iinstallreferenceitem-interface.md)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="05902-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05902-104">語法</span><span class="sxs-lookup"><span data-stu-id="05902-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05902-105">參數</span><span class="sxs-lookup"><span data-stu-id="05902-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="05902-106">脫銷傳回`IInstallReferenceItem`的指標。</span><span class="sxs-lookup"><span data-stu-id="05902-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="05902-107">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="05902-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="05902-108">`dwFlags`必須是0（零）。</span><span class="sxs-lookup"><span data-stu-id="05902-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="05902-109">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="05902-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="05902-110">`pvReserved`必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="05902-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05902-111">需求</span><span class="sxs-lookup"><span data-stu-id="05902-111">Requirements</span></span>  
 <span data-ttu-id="05902-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05902-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05902-113">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="05902-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="05902-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05902-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05902-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05902-115">See also</span></span>

- [<span data-ttu-id="05902-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="05902-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="05902-117">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="05902-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
