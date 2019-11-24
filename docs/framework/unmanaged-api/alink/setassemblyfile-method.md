---
title: SetAssemblyFile 方法
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 1db4c4ab7e47e223a492e08297ac3cedcb3a27eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445600"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="0a688-102">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="0a688-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="0a688-103">Assigns the name of the assembly to be built.</span><span class="sxs-lookup"><span data-stu-id="0a688-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="0a688-104">Not for use when producing unbound modules.</span><span class="sxs-lookup"><span data-stu-id="0a688-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a688-105">語法</span><span class="sxs-lookup"><span data-stu-id="0a688-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a688-106">參數</span><span class="sxs-lookup"><span data-stu-id="0a688-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="0a688-107">Fully qualified name of the manifest file.</span><span class="sxs-lookup"><span data-stu-id="0a688-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="0a688-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="0a688-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="0a688-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0a688-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="0a688-110">Pointer to ID of resulting assembly.</span><span class="sxs-lookup"><span data-stu-id="0a688-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a688-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="0a688-111">Return Value</span></span>  
 <span data-ttu-id="0a688-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="0a688-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a688-113">需求</span><span class="sxs-lookup"><span data-stu-id="0a688-113">Requirements</span></span>  
 <span data-ttu-id="0a688-114">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="0a688-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a688-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="0a688-115">See also</span></span>

- [<span data-ttu-id="0a688-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="0a688-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0a688-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="0a688-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0a688-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="0a688-118">ALink API</span></span>](index.md)
