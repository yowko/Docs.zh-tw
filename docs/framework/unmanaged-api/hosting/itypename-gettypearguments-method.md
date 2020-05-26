---
title: ITypeName::GetTypeArguments 方法
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
ms.openlocfilehash: e059cdddef7926c1359a83bc562146203724aa60
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842100"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="81e51-102">ITypeName::GetTypeArguments 方法</span><span class="sxs-lookup"><span data-stu-id="81e51-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="81e51-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="81e51-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e51-104">語法</span><span class="sxs-lookup"><span data-stu-id="81e51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="81e51-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="81e51-105">Requirements</span></span>  
 <span data-ttu-id="81e51-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81e51-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e51-107">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="81e51-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81e51-108">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="81e51-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81e51-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e51-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e51-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81e51-110">See also</span></span>

- [<span data-ttu-id="81e51-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="81e51-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
