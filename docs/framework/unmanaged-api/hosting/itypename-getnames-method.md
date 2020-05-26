---
title: ITypeName::GetNames 方法
ms.date: 03/30/2017
api_name:
- ITypeName.GetNames
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type:
- apiref
ms.openlocfilehash: 615dad9000b15ed13783ca41cc3c9fe2b563e15c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842149"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="36cc0-102">ITypeName::GetNames 方法</span><span class="sxs-lookup"><span data-stu-id="36cc0-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="36cc0-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="36cc0-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36cc0-104">語法</span><span class="sxs-lookup"><span data-stu-id="36cc0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="36cc0-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="36cc0-105">Requirements</span></span>  
 <span data-ttu-id="36cc0-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36cc0-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36cc0-107">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="36cc0-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36cc0-108">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="36cc0-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36cc0-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36cc0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cc0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36cc0-110">See also</span></span>

- [<span data-ttu-id="36cc0-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="36cc0-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
