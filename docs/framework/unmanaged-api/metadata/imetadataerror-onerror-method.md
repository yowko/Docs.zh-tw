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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ebb7fdbcf8c17991928df2dc621ec651b9cd4f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678716"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="df881-102">IMetaDataError::OnError 方法</span><span class="sxs-lookup"><span data-stu-id="df881-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="df881-103">提供中繼資料合併期間所發生之錯誤的通知。</span><span class="sxs-lookup"><span data-stu-id="df881-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df881-104">語法</span><span class="sxs-lookup"><span data-stu-id="df881-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df881-105">參數</span><span class="sxs-lookup"><span data-stu-id="df881-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="df881-106">[in]HRESULT 錯誤值傳回至呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="df881-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="df881-107">[in]發生錯誤時要合併的程式碼物件的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="df881-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df881-108">需求</span><span class="sxs-lookup"><span data-stu-id="df881-108">Requirements</span></span>  
 <span data-ttu-id="df881-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df881-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df881-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df881-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df881-111">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="df881-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df881-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df881-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df881-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df881-113">See also</span></span>
- [<span data-ttu-id="df881-114">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="df881-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
