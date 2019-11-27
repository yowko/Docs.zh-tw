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
ms.openlocfilehash: afb0c09c09236267be2a999ce5c130feebb52b6f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447901"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="8475f-102">IMetaDataEmit2::SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="8475f-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="8475f-103">將目前的「編輯後繼續」會話的變更儲存至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="8475f-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8475f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8475f-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8475f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8475f-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="8475f-106">在用來儲存變更的檔案名。</span><span class="sxs-lookup"><span data-stu-id="8475f-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="8475f-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="8475f-107">[in] Reserved.</span></span> <span data-ttu-id="8475f-108">必須為零。</span><span class="sxs-lookup"><span data-stu-id="8475f-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8475f-109">需求</span><span class="sxs-lookup"><span data-stu-id="8475f-109">Requirements</span></span>  
 <span data-ttu-id="8475f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8475f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8475f-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8475f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8475f-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="8475f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8475f-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8475f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8475f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8475f-114">See also</span></span>

- [<span data-ttu-id="8475f-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="8475f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="8475f-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="8475f-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
