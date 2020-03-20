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
ms.openlocfilehash: 0ebcab7a759b64bfbb254df1c1aa339cde77d054
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175560"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="bde37-102">IMetaDataEmit2::SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="bde37-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="bde37-103">將當前編輯和繼續會話的更改保存到指定的檔。</span><span class="sxs-lookup"><span data-stu-id="bde37-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde37-104">語法</span><span class="sxs-lookup"><span data-stu-id="bde37-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bde37-105">參數</span><span class="sxs-lookup"><span data-stu-id="bde37-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="bde37-106">[在]要保存的檔案名將發生更改。</span><span class="sxs-lookup"><span data-stu-id="bde37-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="bde37-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="bde37-107">[in] Reserved.</span></span> <span data-ttu-id="bde37-108">必須為零。</span><span class="sxs-lookup"><span data-stu-id="bde37-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bde37-109">需求</span><span class="sxs-lookup"><span data-stu-id="bde37-109">Requirements</span></span>  
 <span data-ttu-id="bde37-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bde37-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bde37-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="bde37-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bde37-112">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bde37-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bde37-113">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bde37-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bde37-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bde37-114">See also</span></span>

- [<span data-ttu-id="bde37-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="bde37-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="bde37-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="bde37-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
