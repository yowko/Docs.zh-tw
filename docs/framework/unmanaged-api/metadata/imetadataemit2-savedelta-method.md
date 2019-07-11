---
title: IMetaDataEmit2::SaveDelta 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 212625fd460e88201dd4799754297861826d3aa7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777140"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="af90e-102">IMetaDataEmit2::SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="af90e-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="af90e-103">將目前的編輯和繼續工作階段的變更儲存至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="af90e-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af90e-104">語法</span><span class="sxs-lookup"><span data-stu-id="af90e-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af90e-105">參數</span><span class="sxs-lookup"><span data-stu-id="af90e-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="af90e-106">[in]用來儲存檔案名稱會變更。</span><span class="sxs-lookup"><span data-stu-id="af90e-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="af90e-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="af90e-107">[in] Reserved.</span></span> <span data-ttu-id="af90e-108">必須是零。</span><span class="sxs-lookup"><span data-stu-id="af90e-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af90e-109">需求</span><span class="sxs-lookup"><span data-stu-id="af90e-109">Requirements</span></span>  
 <span data-ttu-id="af90e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af90e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af90e-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af90e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af90e-112">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="af90e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af90e-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af90e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af90e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af90e-114">See also</span></span>

- [<span data-ttu-id="af90e-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="af90e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="af90e-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="af90e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
