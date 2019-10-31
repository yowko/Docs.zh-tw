---
title: IAssemblyName::SetProperty 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
ms.openlocfilehash: ffa1fa2f5e141728a56f1b598a1aae9602b2ac86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108212"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="73501-102">IAssemblyName::SetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="73501-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="73501-103">設定指定的屬性識別碼所參考之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="73501-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73501-104">語法</span><span class="sxs-lookup"><span data-stu-id="73501-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73501-105">參數</span><span class="sxs-lookup"><span data-stu-id="73501-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="73501-106">在將設定其值之屬性的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="73501-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="73501-107">在要設定 `PropertyId`所參考之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="73501-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="73501-108">在`pvProperty`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="73501-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73501-109">需求</span><span class="sxs-lookup"><span data-stu-id="73501-109">Requirements</span></span>  
 <span data-ttu-id="73501-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73501-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73501-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="73501-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="73501-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73501-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73501-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="73501-113">See also</span></span>

- [<span data-ttu-id="73501-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="73501-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
