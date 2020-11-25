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
ms.openlocfilehash: cde25a9507006c89ef6490c13ae82033f04c2931
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731029"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="f61e5-102">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="f61e5-102">AssemblyComparisonResult Enumeration</span></span>

<span data-ttu-id="f61e5-103">指出兩個元件身分識別的相等（由 [CompareAssemblyIdentity](compareassemblyidentity-function.md) 函式所決定）。</span><span class="sxs-lookup"><span data-stu-id="f61e5-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f61e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="f61e5-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f61e5-105">成員</span><span class="sxs-lookup"><span data-stu-id="f61e5-105">Members</span></span>  
  
|<span data-ttu-id="f61e5-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="f61e5-106">Member name</span></span>|<span data-ttu-id="f61e5-107">描述</span><span class="sxs-lookup"><span data-stu-id="f61e5-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="f61e5-108">表示比較中的所有元件欄位都相符。</span><span class="sxs-lookup"><span data-stu-id="f61e5-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="f61e5-109">表示根據 common language runtime 版本 (CLR) .NET Framework 2.0 版中的元件版本號碼統一，來將元件視為相等。</span><span class="sxs-lookup"><span data-stu-id="f61e5-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="f61e5-110">根據 .NET Framework 2.0 中元件版本號碼的 CLR 統一，表示元件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="f61e5-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="f61e5-111">表示元件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="f61e5-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="f61e5-112">表示以舊版統一的版本號碼為基礎的元件部分相符。</span><span class="sxs-lookup"><span data-stu-id="f61e5-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="f61e5-113">表示單純命名元件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="f61e5-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="f61e5-114">表示根據舊版 .NET Framework 中的版本號碼 CLR 統一，將元件視為相同。</span><span class="sxs-lookup"><span data-stu-id="f61e5-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="f61e5-115">表示兩個簡單命名的元件（其版本號碼已被忽略）之間的相符項。</span><span class="sxs-lookup"><span data-stu-id="f61e5-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="f61e5-116">指出兩個元件之間沒有相符的結果。</span><span class="sxs-lookup"><span data-stu-id="f61e5-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="f61e5-117">指出兩個元件的版本號碼除外，但只有部分相符。</span><span class="sxs-lookup"><span data-stu-id="f61e5-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="f61e5-118">指出兩個元件的版本號碼除外，但不符。</span><span class="sxs-lookup"><span data-stu-id="f61e5-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="f61e5-119">指出不知道非等位的原因。</span><span class="sxs-lookup"><span data-stu-id="f61e5-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f61e5-120">需求</span><span class="sxs-lookup"><span data-stu-id="f61e5-120">Requirements</span></span>  

 <span data-ttu-id="f61e5-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f61e5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f61e5-122">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="f61e5-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f61e5-123">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f61e5-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f61e5-124">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f61e5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61e5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f61e5-125">See also</span></span>

- [<span data-ttu-id="f61e5-126">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="f61e5-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="f61e5-127">融合列舉</span><span class="sxs-lookup"><span data-stu-id="f61e5-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
