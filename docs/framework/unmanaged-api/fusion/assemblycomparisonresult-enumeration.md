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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0086906b23cc65825bbd54a54e544fa9ec7b211e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796262"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="8409a-102">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="8409a-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="8409a-103">表示由[CompareAssemblyIdentity](compareassemblyidentity-function.md)函式決定的兩個元件識別是否相等。</span><span class="sxs-lookup"><span data-stu-id="8409a-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8409a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8409a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8409a-105">成員</span><span class="sxs-lookup"><span data-stu-id="8409a-105">Members</span></span>  
  
|<span data-ttu-id="8409a-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="8409a-106">Member name</span></span>|<span data-ttu-id="8409a-107">說明</span><span class="sxs-lookup"><span data-stu-id="8409a-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="8409a-108">表示比較中的所有元件欄位都相符。</span><span class="sxs-lookup"><span data-stu-id="8409a-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="8409a-109">指出元件會根據 .NET Framework 版本2.0 中元件版本號碼的通用語言執行時間版本（CLR）統一而視為對等。</span><span class="sxs-lookup"><span data-stu-id="8409a-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="8409a-110">根據 .NET Framework 2.0 中元件版本號碼的 CLR 統一，指出元件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="8409a-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="8409a-111">表示元件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="8409a-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="8409a-112">根據版本號碼的舊版統一，指出元件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="8409a-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="8409a-113">表示只有命名元件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="8409a-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="8409a-114">指出元件會根據舊版 .NET Framework 中的 CLR 統一版本號碼，視為對等。</span><span class="sxs-lookup"><span data-stu-id="8409a-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="8409a-115">表示兩個單純命名的元件（其版本號碼已略過）之間的相符項。</span><span class="sxs-lookup"><span data-stu-id="8409a-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="8409a-116">表示兩個元件之間沒有相符的。</span><span class="sxs-lookup"><span data-stu-id="8409a-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="8409a-117">指出兩個元件是否相符，但只符合部分的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="8409a-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="8409a-118">表示兩個元件相符，但不符合其版本號碼。</span><span class="sxs-lookup"><span data-stu-id="8409a-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="8409a-119">指出非等位的原因不是已知的。</span><span class="sxs-lookup"><span data-stu-id="8409a-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8409a-120">需求</span><span class="sxs-lookup"><span data-stu-id="8409a-120">Requirements</span></span>  
 <span data-ttu-id="8409a-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8409a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8409a-122">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="8409a-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8409a-123">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8409a-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8409a-124">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8409a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8409a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8409a-125">See also</span></span>

- [<span data-ttu-id="8409a-126">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="8409a-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="8409a-127">融合列舉</span><span class="sxs-lookup"><span data-stu-id="8409a-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
