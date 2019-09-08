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
ms.openlocfilehash: 1f2f7ba822507a30fe8cd5303f53406d34661833
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796622"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="aebba-102">IAssemblyName::Finalize 方法</span><span class="sxs-lookup"><span data-stu-id="aebba-102">IAssemblyName::Finalize Method</span></span>
<span data-ttu-id="aebba-103">允許這個[IAssemblyName](iassemblyname-interface.md)物件釋放資源，並執行其他清除作業，再呼叫其析構函式。</span><span class="sxs-lookup"><span data-stu-id="aebba-103">Allows this [IAssemblyName](iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebba-104">語法</span><span class="sxs-lookup"><span data-stu-id="aebba-104">Syntax</span></span>  
  
```cpp  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="aebba-105">需求</span><span class="sxs-lookup"><span data-stu-id="aebba-105">Requirements</span></span>  
 <span data-ttu-id="aebba-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aebba-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aebba-107">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="aebba-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="aebba-108">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aebba-108">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebba-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aebba-109">See also</span></span>

- [<span data-ttu-id="aebba-110">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="aebba-110">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
