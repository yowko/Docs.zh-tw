---
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
ms.openlocfilehash: b24f8ed4f5e2c6e0022f5599f2ab8c44a30a561a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129269"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="862cf-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="862cf-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="862cf-103">取得呼叫執行緒上目前例外狀況的 Watson 值區。</span><span class="sxs-lookup"><span data-stu-id="862cf-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="862cf-104">「值區」（ *bucket* ）是與相同程式碼缺失相關的錯誤資料集合。</span><span class="sxs-lookup"><span data-stu-id="862cf-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="862cf-105">*Watson*指的是一組用來收集和分析與例外狀況相關聯之資料的技術。</span><span class="sxs-lookup"><span data-stu-id="862cf-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="862cf-106">語法</span><span class="sxs-lookup"><span data-stu-id="862cf-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="862cf-107">參數</span><span class="sxs-lookup"><span data-stu-id="862cf-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="862cf-108">脫銷[BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)結構的指標，其中包含例外狀況的錯誤資料。</span><span class="sxs-lookup"><span data-stu-id="862cf-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="862cf-109">需求</span><span class="sxs-lookup"><span data-stu-id="862cf-109">Requirements</span></span>  
 <span data-ttu-id="862cf-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="862cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="862cf-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="862cf-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="862cf-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="862cf-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="862cf-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="862cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="862cf-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="862cf-114">See also</span></span>

- [<span data-ttu-id="862cf-115">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="862cf-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
