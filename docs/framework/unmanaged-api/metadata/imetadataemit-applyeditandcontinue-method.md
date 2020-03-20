---
title: IMetaDataEmit::ApplyEditAndContinue 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: f876187624d066b9e672fbf44a984d6d02a54c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175872"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="a95dd-102">IMetaDataEmit::ApplyEditAndContinue 方法</span><span class="sxs-lookup"><span data-stu-id="a95dd-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="a95dd-103">使用在指定的中繼資料中所做的更改更新當前程式集範圍。</span><span class="sxs-lookup"><span data-stu-id="a95dd-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a95dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="a95dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a95dd-105">參數</span><span class="sxs-lookup"><span data-stu-id="a95dd-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="a95dd-106">\[在\]指向[IUnknown](/cpp/atl/iunknown)物件的指標中，該物件表示來自可攜式可執行檔 （PE） 檔中的增量中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a95dd-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="a95dd-107">增量中繼資料是中繼資料塊，包括對模組實際中繼資料副本所做的更改。</span><span class="sxs-lookup"><span data-stu-id="a95dd-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a95dd-108">需求</span><span class="sxs-lookup"><span data-stu-id="a95dd-108">Requirements</span></span>  
 <span data-ttu-id="a95dd-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a95dd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a95dd-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="a95dd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a95dd-111">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a95dd-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a95dd-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a95dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95dd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a95dd-113">See also</span></span>

- [<span data-ttu-id="a95dd-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a95dd-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a95dd-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a95dd-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
