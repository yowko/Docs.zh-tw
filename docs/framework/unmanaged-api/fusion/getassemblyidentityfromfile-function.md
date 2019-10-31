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
ms.openlocfilehash: 50ec5a23db4d2460480bcc3e463ecd88e7470bde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134525"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="6b720-102">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="6b720-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="6b720-103">取得位於指定檔案路徑之元件中具有指定 `IID` 之 `IUnknown` 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="6b720-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b720-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b720-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b720-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b720-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="6b720-106">在所要求元件的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="6b720-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="6b720-107">在要傳回之介面的 `IID`。</span><span class="sxs-lookup"><span data-stu-id="6b720-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="6b720-108">脫銷傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="6b720-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b720-109">需求</span><span class="sxs-lookup"><span data-stu-id="6b720-109">Requirements</span></span>  
 <span data-ttu-id="6b720-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b720-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b720-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="6b720-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6b720-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b720-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b720-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b720-113">See also</span></span>

- [<span data-ttu-id="6b720-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="6b720-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="6b720-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6b720-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
