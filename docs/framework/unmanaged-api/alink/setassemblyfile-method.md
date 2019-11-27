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
# <a name="setassemblyfile-method"></a><span data-ttu-id="609d3-102">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="609d3-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="609d3-103">指派要建立之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="609d3-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="609d3-104">未在產生未系結模組時使用。</span><span class="sxs-lookup"><span data-stu-id="609d3-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="609d3-105">語法</span><span class="sxs-lookup"><span data-stu-id="609d3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="609d3-106">參數</span><span class="sxs-lookup"><span data-stu-id="609d3-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="609d3-107">資訊清單檔的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="609d3-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="609d3-108">[IMetaDataEmit 介面](../metadata/imetadataemit-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="609d3-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="609d3-109">[AssemblyFlags 列舉](../metadata/assemblyflags-enumeration.md)中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="609d3-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="609d3-110">產生之元件的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="609d3-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="609d3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="609d3-111">Return Value</span></span>  
 <span data-ttu-id="609d3-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="609d3-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="609d3-113">需求</span><span class="sxs-lookup"><span data-stu-id="609d3-113">Requirements</span></span>  
 <span data-ttu-id="609d3-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="609d3-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609d3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="609d3-115">See also</span></span>

- [<span data-ttu-id="609d3-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="609d3-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="609d3-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="609d3-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="609d3-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="609d3-118">ALink API</span></span>](index.md)
