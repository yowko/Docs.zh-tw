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
ms.openlocfilehash: adc72eb1b50369e5219798cdb99618abc5e08a00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440385"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="8ffb7-102">ITypeNameFactory::ParseTypeName 方法</span><span class="sxs-lookup"><span data-stu-id="8ffb7-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="8ffb7-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="8ffb7-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ffb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ffb7-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="8ffb7-105">需求</span><span class="sxs-lookup"><span data-stu-id="8ffb7-105">Requirements</span></span>  
 <span data-ttu-id="8ffb7-106">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ffb7-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ffb7-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ffb7-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ffb7-108">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8ffb7-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ffb7-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ffb7-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ffb7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ffb7-110">See Also</span></span>  
 [<span data-ttu-id="8ffb7-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="8ffb7-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
