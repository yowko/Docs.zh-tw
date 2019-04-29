---
title: ITypeNameFactory::ParseTypeName 方法
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbe5f634a5d0580c7e58b03f318da98a0112fa6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765358"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="3a45b-102">ITypeNameFactory::ParseTypeName 方法</span><span class="sxs-lookup"><span data-stu-id="3a45b-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="3a45b-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="3a45b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a45b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a45b-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3a45b-105">需求</span><span class="sxs-lookup"><span data-stu-id="3a45b-105">Requirements</span></span>  
 <span data-ttu-id="3a45b-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a45b-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a45b-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a45b-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a45b-108">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3a45b-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a45b-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a45b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a45b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a45b-110">See also</span></span>

- [<span data-ttu-id="3a45b-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="3a45b-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
