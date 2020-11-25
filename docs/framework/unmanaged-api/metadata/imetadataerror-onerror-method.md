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
ms.openlocfilehash: 6f6e531c99d341eba39939a184d2424256d9e155
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701866"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="539f0-102">IMetaDataError::OnError 方法</span><span class="sxs-lookup"><span data-stu-id="539f0-102">IMetaDataError::OnError Method</span></span>

<span data-ttu-id="539f0-103">提供在中繼資料合併期間發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="539f0-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="539f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="539f0-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="539f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="539f0-105">Parameters</span></span>  

 `hrError`  
 <span data-ttu-id="539f0-106">在傳回給呼叫方法的 HRESULT 錯誤值。</span><span class="sxs-lookup"><span data-stu-id="539f0-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="539f0-107">在發生錯誤時正在合併之程式碼物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="539f0-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="539f0-108">需求</span><span class="sxs-lookup"><span data-stu-id="539f0-108">Requirements</span></span>  

 <span data-ttu-id="539f0-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="539f0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="539f0-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="539f0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="539f0-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="539f0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="539f0-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="539f0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="539f0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="539f0-113">See also</span></span>

- [<span data-ttu-id="539f0-114">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="539f0-114">IMetaDataError Interface</span></span>](imetadataerror-interface.md)
