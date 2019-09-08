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
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796325"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="399f5-102">IsFrameworkAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="399f5-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="399f5-103">取得值，指出指定的元件是否為 managed。</span><span class="sxs-lookup"><span data-stu-id="399f5-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="399f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="399f5-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="399f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="399f5-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="399f5-106">在要檢查之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="399f5-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="399f5-107">脫銷布林值，指出元件是否受管理。</span><span class="sxs-lookup"><span data-stu-id="399f5-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="399f5-108">在Uncanonicalized 字串，其中包含元件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="399f5-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="399f5-109">[in] `pwzFrameworkAssemblyIdentity` 的大小。</span><span class="sxs-lookup"><span data-stu-id="399f5-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="399f5-110">備註</span><span class="sxs-lookup"><span data-stu-id="399f5-110">Remarks</span></span>  
 <span data-ttu-id="399f5-111">`pwzAssemblyReference`參數是字元字串的指標，其中包含元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="399f5-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="399f5-112">如果這個元件是 .NET Framework 的一部分，則`pbIsFrameworkAssembly`參數會包含的布林`true`值。</span><span class="sxs-lookup"><span data-stu-id="399f5-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="399f5-113">如果命名元件不是 .NET Framework 的一部分，或如果`pwzAssemblyReference`參數不是元件的名稱， `pbIsFrameworkAssembly`則會`false`包含的布林值。</span><span class="sxs-lookup"><span data-stu-id="399f5-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="399f5-114">需求</span><span class="sxs-lookup"><span data-stu-id="399f5-114">Requirements</span></span>  
 <span data-ttu-id="399f5-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="399f5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399f5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="399f5-116">See also</span></span>

- [<span data-ttu-id="399f5-117">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="399f5-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
