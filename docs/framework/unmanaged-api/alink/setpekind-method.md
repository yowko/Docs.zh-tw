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
ms.openlocfilehash: dfbc10bdbe633450dee2e27524c29ead21fb739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445542"
---
# <a name="setpekind-method"></a><span data-ttu-id="6f2e4-102">SetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="6f2e4-102">SetPEKind Method</span></span>
<span data-ttu-id="6f2e4-103">決定可移植的可執行檔案類型，可能是電腦特定或電腦中立。</span><span class="sxs-lookup"><span data-stu-id="6f2e4-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f2e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f2e4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="6f2e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f2e4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6f2e4-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6f2e4-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6f2e4-107">要設定 PE 類型的檔案標記。</span><span class="sxs-lookup"><span data-stu-id="6f2e4-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="6f2e4-108">如果 `AssemblyID` 未指出未系結的 .netmodule，則可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="6f2e4-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="6f2e4-109">PE 的類型，如[CorPEKind 列舉](../metadata/corpekind-enumeration.md)所表示。</span><span class="sxs-lookup"><span data-stu-id="6f2e4-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="6f2e4-110">如 NT 標頭所示的目的電腦架構。</span><span class="sxs-lookup"><span data-stu-id="6f2e4-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f2e4-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f2e4-111">Return Value</span></span>  
 <span data-ttu-id="6f2e4-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="6f2e4-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f2e4-113">需求</span><span class="sxs-lookup"><span data-stu-id="6f2e4-113">Requirements</span></span>  
 <span data-ttu-id="6f2e4-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="6f2e4-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2e4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f2e4-115">See also</span></span>

- [<span data-ttu-id="6f2e4-116">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="6f2e4-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="6f2e4-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="6f2e4-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6f2e4-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="6f2e4-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6f2e4-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="6f2e4-119">ALink API</span></span>](index.md)
