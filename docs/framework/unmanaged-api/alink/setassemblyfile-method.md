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
ms.openlocfilehash: 45eed17b91f70d4188d1d89fc91a41455f3e845b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732641"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="de3c5-102">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="de3c5-102">SetAssemblyFile Method</span></span>

<span data-ttu-id="de3c5-103">指派要建立之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="de3c5-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="de3c5-104">無法在產生未系結的模組時使用。</span><span class="sxs-lookup"><span data-stu-id="de3c5-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de3c5-105">語法</span><span class="sxs-lookup"><span data-stu-id="de3c5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="de3c5-106">參數</span><span class="sxs-lookup"><span data-stu-id="de3c5-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="de3c5-107">資訊清單檔案的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="de3c5-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="de3c5-108">[IMetaDataEmit 介面](../metadata/imetadataemit-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="de3c5-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="de3c5-109">[AssemblyFlags 列舉](../metadata/assemblyflags-enumeration.md)中所定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="de3c5-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="de3c5-110">所產生元件的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="de3c5-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de3c5-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="de3c5-111">Return Value</span></span>  

 <span data-ttu-id="de3c5-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="de3c5-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de3c5-113">需求</span><span class="sxs-lookup"><span data-stu-id="de3c5-113">Requirements</span></span>  

 <span data-ttu-id="de3c5-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="de3c5-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3c5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de3c5-115">See also</span></span>

- [<span data-ttu-id="de3c5-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="de3c5-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="de3c5-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="de3c5-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="de3c5-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="de3c5-118">ALink API</span></span>](index.md)
