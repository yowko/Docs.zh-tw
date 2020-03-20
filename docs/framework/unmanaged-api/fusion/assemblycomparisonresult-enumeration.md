---
title: AssemblyComparisonResult 列舉
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178297"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="d2f7d-102">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="d2f7d-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="d2f7d-103">指示由[比較裝配標識](compareassemblyidentity-function.md)函數確定的兩個程式集標識的等效性。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2f7d-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2f7d-104">Syntax</span></span>  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="d2f7d-105">成員</span><span class="sxs-lookup"><span data-stu-id="d2f7d-105">Members</span></span>  
  
|<span data-ttu-id="d2f7d-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="d2f7d-106">Member name</span></span>|<span data-ttu-id="d2f7d-107">描述</span><span class="sxs-lookup"><span data-stu-id="d2f7d-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="d2f7d-108">指示比較中的所有程式集欄位匹配。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="d2f7d-109">指示基於 .NET Framework 版本 2.0 中程式集版本 2.0 中程式集版本編號的通用語言執行階段版本 （CLR） 統一，將程式集視為等效。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="d2f7d-110">指示基於 .NET 框架 2.0 中程式集版本號的 CLR 統一的程式集的部分匹配。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="d2f7d-111">指示程式集的部分匹配。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="d2f7d-112">指示基於版本號的舊統一的程式集的部分匹配。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="d2f7d-113">指示簡單命名程式集的部分匹配。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="d2f7d-114">指示基於 .NET Framework 舊版本中版本號的 CLR 統一，將程式集視為等效。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="d2f7d-115">指示兩個簡單命名的程式集之間的匹配，其版本號被忽略。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="d2f7d-116">指示兩個程式集之間沒有匹配。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="d2f7d-117">指示兩個程式集匹配，但版本號除外，只有部分匹配。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="d2f7d-118">指示兩個程式集匹配，但版本號不匹配。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="d2f7d-119">指示非等價的原因尚不清楚。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2f7d-120">需求</span><span class="sxs-lookup"><span data-stu-id="d2f7d-120">Requirements</span></span>  
 <span data-ttu-id="d2f7d-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f7d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2f7d-122">**標題：** 融合.h</span><span class="sxs-lookup"><span data-stu-id="d2f7d-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d2f7d-123">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d2f7d-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2f7d-124">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2f7d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f7d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f7d-125">See also</span></span>

- [<span data-ttu-id="d2f7d-126">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="d2f7d-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="d2f7d-127">融合列舉</span><span class="sxs-lookup"><span data-stu-id="d2f7d-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
