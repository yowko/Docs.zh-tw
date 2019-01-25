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
ms.openlocfilehash: 3442c61fd6aea23dfcb66fe63ece0b90b61f5580
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741739"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="d2e6f-102">ITypeNameFactory::ParseTypeName 方法</span><span class="sxs-lookup"><span data-stu-id="d2e6f-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="d2e6f-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="d2e6f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2e6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2e6f-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d2e6f-105">需求</span><span class="sxs-lookup"><span data-stu-id="d2e6f-105">Requirements</span></span>  
 <span data-ttu-id="d2e6f-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2e6f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2e6f-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2e6f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2e6f-108">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d2e6f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2e6f-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2e6f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e6f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2e6f-110">See also</span></span>
- [<span data-ttu-id="d2e6f-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d2e6f-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
