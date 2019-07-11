---
title: ITypeName::GetAssemblyName 方法
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81b93675870d73902cf986a64d34d7c270e02203
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780548"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="fb2f6-102">ITypeName::GetAssemblyName 方法</span><span class="sxs-lookup"><span data-stu-id="fb2f6-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="fb2f6-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb2f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fb2f6-105">需求</span><span class="sxs-lookup"><span data-stu-id="fb2f6-105">Requirements</span></span>  
 <span data-ttu-id="fb2f6-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb2f6-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb2f6-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb2f6-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb2f6-108">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fb2f6-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb2f6-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb2f6-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2f6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb2f6-110">See also</span></span>

- [<span data-ttu-id="fb2f6-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="fb2f6-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
