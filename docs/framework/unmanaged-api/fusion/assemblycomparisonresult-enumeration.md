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
ms.openlocfilehash: 03b8ecc996e14263510e2d0a658cec020696c263
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914495"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="42e68-102">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="42e68-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="42e68-103">表示之兩個組件身分識別，對等，由[CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="42e68-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42e68-104">語法</span><span class="sxs-lookup"><span data-stu-id="42e68-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="42e68-105">成員</span><span class="sxs-lookup"><span data-stu-id="42e68-105">Members</span></span>  
  
|<span data-ttu-id="42e68-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="42e68-106">Member name</span></span>|<span data-ttu-id="42e68-107">描述</span><span class="sxs-lookup"><span data-stu-id="42e68-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="42e68-108">表示所有組件欄位比對中。</span><span class="sxs-lookup"><span data-stu-id="42e68-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="42e68-109">指出，組件都視為對等的通用語言執行階段 (CLR) 版本統一的.NET Framework 2.0 版中的組件版本號碼為基礎。</span><span class="sxs-lookup"><span data-stu-id="42e68-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="42e68-110">表示根據.NET Framework 2.0 中的組件版本號碼將 CLR 統一的組件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="42e68-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="42e68-111">指出部分相符的組件。</span><span class="sxs-lookup"><span data-stu-id="42e68-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="42e68-112">表示根據舊版的版本號碼的統一的組件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="42e68-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="42e68-113">指出部分相符的簡單名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="42e68-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="42e68-114">指出，組件視為相同的基礎 CLR 版本對應轉換的舊版本的.NET Framework 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="42e68-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="42e68-115">表示忽略其版本號碼的兩個簡單名稱組件之間相符。</span><span class="sxs-lookup"><span data-stu-id="42e68-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="42e68-116">表示發生在兩個組件之間沒有相符項目。</span><span class="sxs-lookup"><span data-stu-id="42e68-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="42e68-117">指出兩個組件相符除了其版本號碼，只有部分相符。</span><span class="sxs-lookup"><span data-stu-id="42e68-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="42e68-118">指出兩個組件相符除了其版本號碼，不相符。</span><span class="sxs-lookup"><span data-stu-id="42e68-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="42e68-119">指出不相等的原因不明。</span><span class="sxs-lookup"><span data-stu-id="42e68-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42e68-120">需求</span><span class="sxs-lookup"><span data-stu-id="42e68-120">Requirements</span></span>  
 <span data-ttu-id="42e68-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42e68-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42e68-122">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="42e68-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="42e68-123">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="42e68-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42e68-124">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42e68-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e68-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42e68-125">See also</span></span>

- [<span data-ttu-id="42e68-126">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="42e68-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [<span data-ttu-id="42e68-127">融合列舉</span><span class="sxs-lookup"><span data-stu-id="42e68-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
