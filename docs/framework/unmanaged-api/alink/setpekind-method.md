---
title: SetPEKind 方法
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179380"
---
# <a name="setpekind-method"></a><span data-ttu-id="ff860-102">SetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="ff860-102">SetPEKind Method</span></span>
<span data-ttu-id="ff860-103">確定可移植可執行類型，無論是特定于機器還是與機器無關。</span><span class="sxs-lookup"><span data-stu-id="ff860-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff860-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff860-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="ff860-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff860-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ff860-106">程式集的 ID。</span><span class="sxs-lookup"><span data-stu-id="ff860-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ff860-107">要為其設置 PE 類型的檔權杖。</span><span class="sxs-lookup"><span data-stu-id="ff860-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="ff860-108">如果未`AssemblyID`指示未綁定網路模組，則可以為 Null。</span><span class="sxs-lookup"><span data-stu-id="ff860-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="ff860-109">PE 的類型，如[CorPEKind 枚舉](../metadata/corpekind-enumeration.md)所示。</span><span class="sxs-lookup"><span data-stu-id="ff860-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="ff860-110">目的電腦體系結構，如 NT 標頭中所示。</span><span class="sxs-lookup"><span data-stu-id="ff860-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff860-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ff860-111">Return Value</span></span>  
 <span data-ttu-id="ff860-112">如果方法成功，則返回S_OK。</span><span class="sxs-lookup"><span data-stu-id="ff860-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff860-113">需求</span><span class="sxs-lookup"><span data-stu-id="ff860-113">Requirements</span></span>  
 <span data-ttu-id="ff860-114">需要 alink.h.</span><span class="sxs-lookup"><span data-stu-id="ff860-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff860-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff860-115">See also</span></span>

- [<span data-ttu-id="ff860-116">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="ff860-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="ff860-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ff860-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ff860-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ff860-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ff860-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="ff860-119">ALink API</span></span>](index.md)
