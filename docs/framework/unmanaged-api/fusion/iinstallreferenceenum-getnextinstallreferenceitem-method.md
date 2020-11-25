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
ms.openlocfilehash: e093de7d2c2388274cbe9ebbe46084ee6ae3ff8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721097"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="59f00-102">IInstallReferenceEnum::GetNextInstallReferenceItem 方法</span><span class="sxs-lookup"><span data-stu-id="59f00-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>

<span data-ttu-id="59f00-103">取得這個[IInstallReferenceEnum](iinstallreferenceenum-interface.md)物件中所包含下一個[IInstallReferenceItem](iinstallreferenceitem-interface.md)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="59f00-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59f00-104">語法</span><span class="sxs-lookup"><span data-stu-id="59f00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59f00-105">參數</span><span class="sxs-lookup"><span data-stu-id="59f00-105">Parameters</span></span>  

 `ppRefItem`  
 <span data-ttu-id="59f00-106">擴展傳回的 `IInstallReferenceItem` 指標。</span><span class="sxs-lookup"><span data-stu-id="59f00-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="59f00-107">在保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="59f00-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="59f00-108">`dwFlags` 必須為 0 (零) 。</span><span class="sxs-lookup"><span data-stu-id="59f00-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="59f00-109">在保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="59f00-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="59f00-110">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="59f00-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59f00-111">需求</span><span class="sxs-lookup"><span data-stu-id="59f00-111">Requirements</span></span>  

 <span data-ttu-id="59f00-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59f00-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59f00-113">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="59f00-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="59f00-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59f00-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f00-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59f00-115">See also</span></span>

- [<span data-ttu-id="59f00-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="59f00-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="59f00-117">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="59f00-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
