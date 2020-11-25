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
ms.openlocfilehash: 64751032c017473ffd82248b310b14c087f74129
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727831"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="00392-102">ITypeName::GetModifiers 方法</span><span class="sxs-lookup"><span data-stu-id="00392-102">ITypeName::GetModifiers Method</span></span>

<span data-ttu-id="00392-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="00392-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00392-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="00392-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="00392-105">需求</span><span class="sxs-lookup"><span data-stu-id="00392-105">Requirements</span></span>  

 <span data-ttu-id="00392-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00392-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00392-107">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="00392-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00392-108">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="00392-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00392-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00392-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00392-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00392-110">See also</span></span>

- [<span data-ttu-id="00392-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="00392-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
