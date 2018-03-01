---
title: "AssemblyComparisonResult 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2c38561a804a331df102a600d4b0b0f6312aaa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="1e5c1-102">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="1e5c1-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="1e5c1-103">指出兩個組件識別是否相等由[CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e5c1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1e5c1-105">成員</span><span class="sxs-lookup"><span data-stu-id="1e5c1-105">Members</span></span>  
  
|<span data-ttu-id="1e5c1-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="1e5c1-106">Member name</span></span>|<span data-ttu-id="1e5c1-107">描述</span><span class="sxs-lookup"><span data-stu-id="1e5c1-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="1e5c1-108">表示所有組件欄位比對中。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="1e5c1-109">指出的組件都會被視為相等的通用語言執行階段 (CLR) 版本統一的.NET Framework 2.0 版中的組件版本號碼為基礎。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="1e5c1-110">表示 CLR 統一的.NET Framework 2.0 中的組件版本號碼為基礎的組件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="1e5c1-111">表示組件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="1e5c1-112">表示根據舊的版本號碼的統一的組件的部分相符。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="1e5c1-113">指出部分相符的簡單名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="1e5c1-114">指出的組件都會被視為相等 CLR 統一的舊版本的.NET framework 的版本號碼為基礎。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="1e5c1-115">表示兩個簡單名稱的組件，已忽略其版本號碼之間相符。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="1e5c1-116">指出兩個組件之間沒有相符項目。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="1e5c1-117">指出兩個組件相符除了其版本號碼，只有部分相符。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="1e5c1-118">指出兩個組件相符除了其版本號碼，並不相符。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="1e5c1-119">指出不相等的原因不明。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e5c1-120">需求</span><span class="sxs-lookup"><span data-stu-id="1e5c1-120">Requirements</span></span>  
 <span data-ttu-id="1e5c1-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e5c1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e5c1-122">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1e5c1-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1e5c1-123">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1e5c1-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e5c1-124">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e5c1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5c1-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e5c1-125">See Also</span></span>  
 [<span data-ttu-id="1e5c1-126">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="1e5c1-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [<span data-ttu-id="1e5c1-127">融合列舉</span><span class="sxs-lookup"><span data-stu-id="1e5c1-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
