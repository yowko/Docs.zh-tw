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
ms.openlocfilehash: 91e73f8e3d2e3c372d3fe1c4fd4fccf6ff67b363
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727805"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="ae73f-102">ITypeName::GetNames 方法</span><span class="sxs-lookup"><span data-stu-id="ae73f-102">ITypeName::GetNames Method</span></span>

<span data-ttu-id="ae73f-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="ae73f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae73f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae73f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ae73f-105">需求</span><span class="sxs-lookup"><span data-stu-id="ae73f-105">Requirements</span></span>  

 <span data-ttu-id="ae73f-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae73f-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae73f-107">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ae73f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae73f-108">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ae73f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae73f-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae73f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae73f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae73f-110">See also</span></span>

- [<span data-ttu-id="ae73f-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ae73f-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
