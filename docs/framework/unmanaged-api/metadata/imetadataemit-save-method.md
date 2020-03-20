---
title: IMetaDataEmit::Save 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: 76f18336808e6832b2ded94349efd7948f23a1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175690"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="179e0-102">IMetaDataEmit::Save 方法</span><span class="sxs-lookup"><span data-stu-id="179e0-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="179e0-103">將當前作用域中的所有中繼資料保存到指定位址的檔。</span><span class="sxs-lookup"><span data-stu-id="179e0-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="179e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="179e0-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="179e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="179e0-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="179e0-106">[在]要保存到的檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="179e0-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="179e0-107">如果此值為空，記憶體中的副本將保存到使用的最後一個位置。</span><span class="sxs-lookup"><span data-stu-id="179e0-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="179e0-108">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="179e0-108">[in] Reserved.</span></span> <span data-ttu-id="179e0-109">必須為零。</span><span class="sxs-lookup"><span data-stu-id="179e0-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="179e0-110">需求</span><span class="sxs-lookup"><span data-stu-id="179e0-110">Requirements</span></span>  
 <span data-ttu-id="179e0-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="179e0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="179e0-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="179e0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="179e0-113">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="179e0-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="179e0-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="179e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="179e0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="179e0-115">See also</span></span>

- [<span data-ttu-id="179e0-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="179e0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="179e0-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="179e0-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
