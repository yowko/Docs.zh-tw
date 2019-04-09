---
title: IAssemblyName::Finalize 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.Finalize
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Finalize
helpviewer_keywords:
- Finalize method [.NET Framework fusion]
- IAssemblyName::Finalize method [.NET Framework fusion]
ms.assetid: 610e792d-98ef-411f-90b0-5b9a3813f547
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4db24977d46277bc16a8800b0c4f7a550747cb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206521"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="0ca3f-102">IAssemblyName::Finalize 方法</span><span class="sxs-lookup"><span data-stu-id="0ca3f-102">IAssemblyName::Finalize Method</span></span>
<span data-ttu-id="0ca3f-103">這可讓[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件釋放資源並呼叫其解構函式之前執行其他清除作業。</span><span class="sxs-lookup"><span data-stu-id="0ca3f-103">Allows this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ca3f-104">Syntax</span></span>  
  
```  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0ca3f-105">需求</span><span class="sxs-lookup"><span data-stu-id="0ca3f-105">Requirements</span></span>  
 <span data-ttu-id="0ca3f-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca3f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca3f-107">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0ca3f-107">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="0ca3f-108">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0ca3f-108">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0ca3f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ca3f-109">See also</span></span>

- [<span data-ttu-id="0ca3f-110">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="0ca3f-110">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
