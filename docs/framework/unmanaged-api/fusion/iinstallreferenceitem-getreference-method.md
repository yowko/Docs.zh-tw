---
title: IInstallReferenceItem::GetReference 方法
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd0a554535122b81f5812102c7951f56b294796a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757673"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="407a3-102">IInstallReferenceItem::GetReference 方法</span><span class="sxs-lookup"><span data-stu-id="407a3-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="407a3-103">取得指標[FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)所表示的結構[IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="407a3-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="407a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="407a3-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="407a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="407a3-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="407a3-106">[out]傳回`FUSION_INSTALL_REFERENCE`指標。</span><span class="sxs-lookup"><span data-stu-id="407a3-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="407a3-107">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="407a3-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="407a3-108">`dwFlags` 必須是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="407a3-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="407a3-109">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="407a3-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="407a3-110">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="407a3-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="407a3-111">需求</span><span class="sxs-lookup"><span data-stu-id="407a3-111">Requirements</span></span>  
 <span data-ttu-id="407a3-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="407a3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="407a3-113">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="407a3-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="407a3-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="407a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407a3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="407a3-115">See also</span></span>

- [<span data-ttu-id="407a3-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="407a3-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="407a3-117">FUSION_INSTALL_REFERENCE 結構</span><span class="sxs-lookup"><span data-stu-id="407a3-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
