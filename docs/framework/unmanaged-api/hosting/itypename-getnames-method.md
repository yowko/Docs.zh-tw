---
title: ITypeName::GetNames 方法
ms.date: 03/30/2017
api_name:
- ITypeName.GetNames
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28076a36880febad20d457ff5a6b290de3d6f173
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121546"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="71352-102">ITypeName::GetNames 方法</span><span class="sxs-lookup"><span data-stu-id="71352-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="71352-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="71352-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71352-104">語法</span><span class="sxs-lookup"><span data-stu-id="71352-104">Syntax</span></span>  
  
```  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="71352-105">需求</span><span class="sxs-lookup"><span data-stu-id="71352-105">Requirements</span></span>  
 <span data-ttu-id="71352-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71352-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71352-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71352-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71352-108">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="71352-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="71352-109">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="71352-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71352-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71352-110">See also</span></span>

- [<span data-ttu-id="71352-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="71352-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
