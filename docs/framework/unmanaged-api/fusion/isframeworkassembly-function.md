---
title: IsFrameworkAssembly 函式
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3fd130759ab11b54b597d5c099c33dab93070ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429246"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="37a93-102">IsFrameworkAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="37a93-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="37a93-103">取得值，指出指定的組件是否為 managed。</span><span class="sxs-lookup"><span data-stu-id="37a93-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37a93-104">語法</span><span class="sxs-lookup"><span data-stu-id="37a93-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37a93-105">參數</span><span class="sxs-lookup"><span data-stu-id="37a93-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="37a93-106">[in]若要檢查組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="37a93-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="37a93-107">[out]布林值，指出是否為 managed 組件。</span><span class="sxs-lookup"><span data-stu-id="37a93-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="37a93-108">[in]Uncanonicalized 的字串，包含組件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="37a93-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="37a93-109">[in] `pwzFrameworkAssemblyIdentity` 的大小。</span><span class="sxs-lookup"><span data-stu-id="37a93-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37a93-110">備註</span><span class="sxs-lookup"><span data-stu-id="37a93-110">Remarks</span></span>  
 <span data-ttu-id="37a93-111">`pwzAssemblyReference`參數是指向字元字串，包含組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="37a93-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="37a93-112">如果這個組件是.NET framework 的一部分`pbIsFrameworkAssembly`參數會包含布林值`true`。</span><span class="sxs-lookup"><span data-stu-id="37a93-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="37a93-113">如果具名組件不是.NET framework 的一部分，或如果`pwzAssemblyReference`參數無法命名組件，`pbIsFrameworkAssembly`就會包含布林值`false`。</span><span class="sxs-lookup"><span data-stu-id="37a93-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37a93-114">需求</span><span class="sxs-lookup"><span data-stu-id="37a93-114">Requirements</span></span>  
 <span data-ttu-id="37a93-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37a93-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a93-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37a93-116">See Also</span></span>  
 [<span data-ttu-id="37a93-117">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="37a93-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
