---
title: IAssemblyName::GetProperty 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: 3a6f19d9fc90972e767625fadf30cc4af50d9017
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727883"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="cb359-102">IAssemblyName::GetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="cb359-102">IAssemblyName::GetProperty Method</span></span>

<span data-ttu-id="cb359-103">取得指定之屬性識別碼所參考之屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="cb359-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb359-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb359-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb359-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb359-105">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="cb359-106">在所要求屬性的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb359-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="cb359-107">擴展傳回的屬性資料。</span><span class="sxs-lookup"><span data-stu-id="cb359-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="cb359-108">[in，out]的大小（以位元組為單位） `pvProperty` 。</span><span class="sxs-lookup"><span data-stu-id="cb359-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb359-109">需求</span><span class="sxs-lookup"><span data-stu-id="cb359-109">Requirements</span></span>  

 <span data-ttu-id="cb359-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb359-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb359-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="cb359-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cb359-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb359-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb359-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb359-113">See also</span></span>

- [<span data-ttu-id="cb359-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="cb359-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
