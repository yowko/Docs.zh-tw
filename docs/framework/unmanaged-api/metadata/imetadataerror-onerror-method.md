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
ms.openlocfilehash: 489fa217744e41ccb5d27d088790131c15e1ee52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177391"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="cf028-102">IMetaDataError::OnError 方法</span><span class="sxs-lookup"><span data-stu-id="cf028-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="cf028-103">提供中繼資料合併期間發生的錯誤通知。</span><span class="sxs-lookup"><span data-stu-id="cf028-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf028-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf028-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf028-105">參數</span><span class="sxs-lookup"><span data-stu-id="cf028-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="cf028-106">[在]HRESULT 錯誤值返回到調用方法。</span><span class="sxs-lookup"><span data-stu-id="cf028-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="cf028-107">[在]發生錯誤時正在合併的代碼物件的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="cf028-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf028-108">需求</span><span class="sxs-lookup"><span data-stu-id="cf028-108">Requirements</span></span>  
 <span data-ttu-id="cf028-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf028-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf028-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="cf028-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf028-111">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cf028-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf028-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf028-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf028-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf028-113">See also</span></span>

- [<span data-ttu-id="cf028-114">IMetaDataError 介面</span><span class="sxs-lookup"><span data-stu-id="cf028-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
