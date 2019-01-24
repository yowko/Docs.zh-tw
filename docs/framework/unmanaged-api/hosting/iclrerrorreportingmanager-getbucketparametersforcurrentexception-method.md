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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec7e303e5145e16f4c17074d557410ffe4521c20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549833"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="8e44f-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="8e44f-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="8e44f-103">取得目前的例外狀況，在呼叫執行緒上的 Watson 值區。</span><span class="sxs-lookup"><span data-stu-id="8e44f-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="8e44f-104">A*貯體*是相同的程式碼缺失相關的錯誤資料的集合。</span><span class="sxs-lookup"><span data-stu-id="8e44f-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="8e44f-105">*Watson*是指一組技術可用於收集和分析與例外狀況相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="8e44f-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e44f-106">語法</span><span class="sxs-lookup"><span data-stu-id="8e44f-106">Syntax</span></span>  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e44f-107">參數</span><span class="sxs-lookup"><span data-stu-id="8e44f-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="8e44f-108">[out]指標[BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)包含例外狀況的錯誤資料的結構。</span><span class="sxs-lookup"><span data-stu-id="8e44f-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e44f-109">需求</span><span class="sxs-lookup"><span data-stu-id="8e44f-109">Requirements</span></span>  
 <span data-ttu-id="8e44f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e44f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e44f-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8e44f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e44f-112">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8e44f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e44f-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e44f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e44f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e44f-114">See also</span></span>
- [<span data-ttu-id="8e44f-115">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="8e44f-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
