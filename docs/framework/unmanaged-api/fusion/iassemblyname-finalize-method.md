---
title: "IAssemblyName::Finalize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.Finalize
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::Finalize
helpviewer_keywords:
- Finalize method [.NET Framework fusion]
- IAssemblyName::Finalize method [.NET Framework fusion]
ms.assetid: 610e792d-98ef-411f-90b0-5b9a3813f547
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 137c9341dabeb6b7efd029cda5188fbc25308f1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="67191-102">IAssemblyName::Finalize 方法</span><span class="sxs-lookup"><span data-stu-id="67191-102">IAssemblyName::Finalize Method</span></span>
<span data-ttu-id="67191-103">允許您為此[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件釋放資源並呼叫其解構函式之前執行其他清除作業。</span><span class="sxs-lookup"><span data-stu-id="67191-103">Allows this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67191-104">語法</span><span class="sxs-lookup"><span data-stu-id="67191-104">Syntax</span></span>  
  
```  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="67191-105">需求</span><span class="sxs-lookup"><span data-stu-id="67191-105">Requirements</span></span>  
 <span data-ttu-id="67191-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67191-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67191-107">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="67191-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="67191-108">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67191-108">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67191-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67191-109">See Also</span></span>  
 [<span data-ttu-id="67191-110">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="67191-110">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
