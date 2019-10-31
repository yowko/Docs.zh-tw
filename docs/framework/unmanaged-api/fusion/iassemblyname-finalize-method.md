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
ms.openlocfilehash: 15c421471704ffc085da2af6ac74350bd099fdb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134352"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="75323-102">IAssemblyName::Finalize 方法</span><span class="sxs-lookup"><span data-stu-id="75323-102">IAssemblyName::Finalize Method</span></span>
<span data-ttu-id="75323-103">允許這個[IAssemblyName](iassemblyname-interface.md)物件釋放資源，並執行其他清除作業，再呼叫其析構函式。</span><span class="sxs-lookup"><span data-stu-id="75323-103">Allows this [IAssemblyName](iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75323-104">語法</span><span class="sxs-lookup"><span data-stu-id="75323-104">Syntax</span></span>  
  
```cpp  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="75323-105">需求</span><span class="sxs-lookup"><span data-stu-id="75323-105">Requirements</span></span>  
 <span data-ttu-id="75323-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75323-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75323-107">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="75323-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="75323-108">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75323-108">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75323-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="75323-109">See also</span></span>

- [<span data-ttu-id="75323-110">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="75323-110">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
