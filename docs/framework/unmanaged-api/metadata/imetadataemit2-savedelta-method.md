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
ms.openlocfilehash: ab2f30c485a755d4788926c13c2608e55a716c5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704262"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="12fc6-102">IMetaDataEmit2::SaveDelta 方法</span><span class="sxs-lookup"><span data-stu-id="12fc6-102">IMetaDataEmit2::SaveDelta Method</span></span>

<span data-ttu-id="12fc6-103">將目前的編輯後繼續會話的變更儲存至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="12fc6-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12fc6-104">語法</span><span class="sxs-lookup"><span data-stu-id="12fc6-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12fc6-105">參數</span><span class="sxs-lookup"><span data-stu-id="12fc6-105">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="12fc6-106">在用來儲存變更的檔案名。</span><span class="sxs-lookup"><span data-stu-id="12fc6-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="12fc6-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="12fc6-107">[in] Reserved.</span></span> <span data-ttu-id="12fc6-108">必須為零。</span><span class="sxs-lookup"><span data-stu-id="12fc6-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12fc6-109">需求</span><span class="sxs-lookup"><span data-stu-id="12fc6-109">Requirements</span></span>  

 <span data-ttu-id="12fc6-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12fc6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12fc6-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="12fc6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12fc6-112">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="12fc6-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12fc6-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12fc6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12fc6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12fc6-114">See also</span></span>

- [<span data-ttu-id="12fc6-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="12fc6-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="12fc6-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="12fc6-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
