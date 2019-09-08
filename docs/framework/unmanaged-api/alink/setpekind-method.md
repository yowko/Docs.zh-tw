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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a48dbd38d357b668c2794ae6305ceb9cad3dcf4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787187"
---
# <a name="setpekind-method"></a><span data-ttu-id="c4f61-102">SetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="c4f61-102">SetPEKind Method</span></span>
<span data-ttu-id="c4f61-103">決定可移植的可執行檔案類型，可能是電腦特定或電腦中立。</span><span class="sxs-lookup"><span data-stu-id="c4f61-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f61-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4f61-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="c4f61-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4f61-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c4f61-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c4f61-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c4f61-107">要設定 PE 類型的檔案標記。</span><span class="sxs-lookup"><span data-stu-id="c4f61-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="c4f61-108">如果未指出未`AssemblyID`系結的 .netmodule，則可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="c4f61-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="c4f61-109">PE 的類型，如[CorPEKind 列舉](../metadata/corpekind-enumeration.md)所表示。</span><span class="sxs-lookup"><span data-stu-id="c4f61-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="c4f61-110">如 NT 標頭所示的目的電腦架構。</span><span class="sxs-lookup"><span data-stu-id="c4f61-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4f61-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c4f61-111">Return Value</span></span>  
 <span data-ttu-id="c4f61-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c4f61-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4f61-113">需求</span><span class="sxs-lookup"><span data-stu-id="c4f61-113">Requirements</span></span>  
 <span data-ttu-id="c4f61-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="c4f61-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f61-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4f61-115">See also</span></span>

- [<span data-ttu-id="c4f61-116">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="c4f61-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="c4f61-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c4f61-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c4f61-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c4f61-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c4f61-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="c4f61-119">ALink API</span></span>](index.md)
