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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2657ac619bb86bc200de9ce229bf82e4339f78d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796290"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="b2580-102">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="b2580-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="b2580-103">取得具有指定之元件`IUnknown` `IID`中指定檔案路徑之物件的指標。</span><span class="sxs-lookup"><span data-stu-id="b2580-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2580-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2580-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2580-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2580-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="b2580-106">在所要求元件的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="b2580-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="b2580-107">在要`IID`傳回之介面的。</span><span class="sxs-lookup"><span data-stu-id="b2580-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="b2580-108">脫銷傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="b2580-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2580-109">需求</span><span class="sxs-lookup"><span data-stu-id="b2580-109">Requirements</span></span>  
 <span data-ttu-id="b2580-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2580-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2580-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="b2580-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b2580-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2580-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2580-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2580-113">See also</span></span>

- [<span data-ttu-id="b2580-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="b2580-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="b2580-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="b2580-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
