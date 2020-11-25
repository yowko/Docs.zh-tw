---
title: GetAssemblyIdentityFromFile 函式
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 9580dd3bc5a7279549e8deadac95d35a33da74f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724477"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="e2a2b-102">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="e2a2b-102">GetAssemblyIdentityFromFile Function</span></span>

<span data-ttu-id="e2a2b-103">取得物件的指標，該 `IUnknown` 物件具有在 `IID` 指定檔案路徑的元件中指定的。</span><span class="sxs-lookup"><span data-stu-id="e2a2b-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2a2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2a2b-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2a2b-105">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="e2a2b-106">在所要求元件的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="e2a2b-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="e2a2b-107">在 `IID` 要傳回之介面的。</span><span class="sxs-lookup"><span data-stu-id="e2a2b-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="e2a2b-108">擴展傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e2a2b-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2a2b-109">需求</span><span class="sxs-lookup"><span data-stu-id="e2a2b-109">Requirements</span></span>  

 <span data-ttu-id="e2a2b-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a2b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a2b-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="e2a2b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e2a2b-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a2b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a2b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2a2b-113">See also</span></span>

- [<span data-ttu-id="e2a2b-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="e2a2b-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="e2a2b-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e2a2b-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
