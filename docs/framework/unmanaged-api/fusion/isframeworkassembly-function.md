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
ms.openlocfilehash: 828c7660d6c006e700302d119ce4caf7d76e5d84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728559"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="de184-102">IsFrameworkAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="de184-102">IsFrameworkAssembly Function</span></span>

<span data-ttu-id="de184-103">取得值，這個值會指出指定的元件是否為 managed。</span><span class="sxs-lookup"><span data-stu-id="de184-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de184-104">語法</span><span class="sxs-lookup"><span data-stu-id="de184-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="de184-105">參數</span><span class="sxs-lookup"><span data-stu-id="de184-105">Parameters</span></span>  

 `pwzAssemblyReference`  
 <span data-ttu-id="de184-106">在要檢查的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="de184-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="de184-107">擴展指出元件是否受管理的布林值。</span><span class="sxs-lookup"><span data-stu-id="de184-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="de184-108">在Uncanonicalized 字串，其中包含元件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="de184-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="de184-109">[in] `pwzFrameworkAssemblyIdentity` 的大小。</span><span class="sxs-lookup"><span data-stu-id="de184-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de184-110">備註</span><span class="sxs-lookup"><span data-stu-id="de184-110">Remarks</span></span>  

 <span data-ttu-id="de184-111">`pwzAssemblyReference`參數是包含元件名稱的字元字串指標。</span><span class="sxs-lookup"><span data-stu-id="de184-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="de184-112">如果這個元件是 .NET Framework 的一部分， `pbIsFrameworkAssembly` 參數將包含的布林值 `true` 。</span><span class="sxs-lookup"><span data-stu-id="de184-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="de184-113">如果命名的元件不是 .NET Framework 的一部分，或如果參數未 `pwzAssemblyReference` 命名元件， `pbIsFrameworkAssembly` 將會包含的布林值 `false` 。</span><span class="sxs-lookup"><span data-stu-id="de184-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de184-114">需求</span><span class="sxs-lookup"><span data-stu-id="de184-114">Requirements</span></span>  

 <span data-ttu-id="de184-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de184-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de184-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de184-116">See also</span></span>

- [<span data-ttu-id="de184-117">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="de184-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
