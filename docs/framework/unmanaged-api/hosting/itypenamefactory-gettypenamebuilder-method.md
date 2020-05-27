---
title: ITypeNameFactory::GetTypeNameBuilder 方法
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.GetTypeNameBuilder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeNameBuilder
helpviewer_keywords:
- ITypeNameFactory::GetTypeNameBuilder method [.NET Framework hosting]
- GetTypeNameBuilder method [.NET Framework hosting]
ms.assetid: c682f744-996e-43c7-a9ea-c57cbc755398
topic_type:
- apiref
ms.openlocfilehash: bbf84ffbee7d504f7fc6a902285b43857f0ac4d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008621"
---
# <a name="itypenamefactorygettypenamebuilder-method"></a><span data-ttu-id="4e07c-102">ITypeNameFactory::GetTypeNameBuilder 方法</span><span class="sxs-lookup"><span data-stu-id="4e07c-102">ITypeNameFactory::GetTypeNameBuilder Method</span></span>
<span data-ttu-id="4e07c-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="4e07c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e07c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e07c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeNameBuilder (  
    [out, retval] ITypeNameBuilder** ppTypeBuilder  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4e07c-105">需求</span><span class="sxs-lookup"><span data-stu-id="4e07c-105">Requirements</span></span>  
 <span data-ttu-id="4e07c-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e07c-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e07c-107">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4e07c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e07c-108">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4e07c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e07c-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e07c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e07c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e07c-110">See also</span></span>

- [<span data-ttu-id="4e07c-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4e07c-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
