---
title: IMetaDataEmit2::GetDeltaSaveSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 24fe8fd65b36e133b767cd07c8602aa1ea7b9dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493093"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="9db8f-102">IMetaDataEmit2::GetDeltaSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="9db8f-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="9db8f-103">取得值，指出目前的「編輯後繼續」會話所產生之中繼資料大小的任何變更。</span><span class="sxs-lookup"><span data-stu-id="9db8f-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9db8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9db8f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9db8f-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="9db8f-106">在其中一個[CorSaveSize](corsavesize-enumeration.md)值，表示所需的精確度層級。</span><span class="sxs-lookup"><span data-stu-id="9db8f-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="9db8f-107">針對 .NET Framework 版本2.0，會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="9db8f-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="9db8f-108">脫銷中繼資料大小的變更。</span><span class="sxs-lookup"><span data-stu-id="9db8f-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db8f-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="9db8f-109">Requirements</span></span>  
 <span data-ttu-id="9db8f-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9db8f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9db8f-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="9db8f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9db8f-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="9db8f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9db8f-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9db8f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db8f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9db8f-114">See also</span></span>

- [<span data-ttu-id="9db8f-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="9db8f-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="9db8f-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9db8f-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
