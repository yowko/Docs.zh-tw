---
title: IMetaDataImport::GetModuleFromScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 4e2b2501b6b7117cefcfa43511ef20f25106bb42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503578"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="f8784-102">IMetaDataImport::GetModuleFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="f8784-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="f8784-103">取得目前中繼資料範圍中所參考之模組的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="f8784-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8784-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8784-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8784-105">參數</span><span class="sxs-lookup"><span data-stu-id="f8784-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="f8784-106">脫銷Token 的指標，代表目前中繼資料範圍中參考的模組。</span><span class="sxs-lookup"><span data-stu-id="f8784-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8784-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="f8784-107">Requirements</span></span>  
 <span data-ttu-id="f8784-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8784-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8784-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f8784-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8784-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f8784-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8784-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8784-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8784-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8784-112">See also</span></span>

- [<span data-ttu-id="f8784-113">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f8784-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f8784-114">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f8784-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
