---
title: ITypeName::GetModifiers 方法
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: c96764749a766f3b4bbff4cf6512677a47197f4c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095838"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="ab656-102">ITypeName::GetModifiers 方法</span><span class="sxs-lookup"><span data-stu-id="ab656-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="ab656-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="ab656-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab656-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab656-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ab656-105">需求</span><span class="sxs-lookup"><span data-stu-id="ab656-105">Requirements</span></span>  
 <span data-ttu-id="ab656-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab656-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab656-107">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ab656-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab656-108">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ab656-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab656-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab656-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab656-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab656-110">See also</span></span>

- [<span data-ttu-id="ab656-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ab656-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
