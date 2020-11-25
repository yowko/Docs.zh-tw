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
ms.openlocfilehash: 842b878fac1e2590eb6ea0b29ebee0d46e818474
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727922"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="829cd-102">IAssemblyName::Finalize 方法</span><span class="sxs-lookup"><span data-stu-id="829cd-102">IAssemblyName::Finalize Method</span></span>

<span data-ttu-id="829cd-103">允許這個 [IAssemblyName](iassemblyname-interface.md) 物件釋放資源並執行其他清除作業，然後再呼叫它的函式。</span><span class="sxs-lookup"><span data-stu-id="829cd-103">Allows this [IAssemblyName](iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="829cd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="829cd-104">Syntax</span></span>  
  
```cpp  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="829cd-105">需求</span><span class="sxs-lookup"><span data-stu-id="829cd-105">Requirements</span></span>  

 <span data-ttu-id="829cd-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="829cd-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="829cd-107">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="829cd-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="829cd-108">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="829cd-108">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="829cd-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="829cd-109">See also</span></span>

- [<span data-ttu-id="829cd-110">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="829cd-110">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
