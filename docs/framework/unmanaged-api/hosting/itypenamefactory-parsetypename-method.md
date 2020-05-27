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
ms.openlocfilehash: 1d00d150f98e44fb5c6484378266b7d9b238f4a9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008582"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="3fef7-102">ITypeNameFactory::ParseTypeName 方法</span><span class="sxs-lookup"><span data-stu-id="3fef7-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="3fef7-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="3fef7-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fef7-104">語法</span><span class="sxs-lookup"><span data-stu-id="3fef7-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3fef7-105">需求</span><span class="sxs-lookup"><span data-stu-id="3fef7-105">Requirements</span></span>  
 <span data-ttu-id="3fef7-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3fef7-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fef7-107">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="3fef7-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fef7-108">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3fef7-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fef7-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fef7-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fef7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fef7-110">See also</span></span>

- [<span data-ttu-id="3fef7-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="3fef7-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
