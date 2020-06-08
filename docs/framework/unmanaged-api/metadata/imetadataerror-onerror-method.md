---
title: IMetaDataError::OnError 方法
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: d2252f58af1a319d953fb320a99fad1cfec3dca0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492704"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="e7af3-102">IMetaDataError::OnError 方法</span><span class="sxs-lookup"><span data-stu-id="e7af3-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="e7af3-103">提供中繼資料合併期間發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="e7af3-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7af3-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7af3-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7af3-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7af3-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="e7af3-106">在傳回給呼叫方法的 HRESULT 錯誤值。</span><span class="sxs-lookup"><span data-stu-id="e7af3-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="e7af3-107">在發生錯誤時，所合併之程式碼物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="e7af3-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7af3-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="e7af3-108">Requirements</span></span>  
 <span data-ttu-id="e7af3-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7af3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7af3-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e7af3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7af3-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="e7af3-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7af3-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7af3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7af3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7af3-113">See also</span></span>

- [<span data-ttu-id="e7af3-114">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="e7af3-114">IMetaDataError Interface</span></span>](imetadataerror-interface.md)
