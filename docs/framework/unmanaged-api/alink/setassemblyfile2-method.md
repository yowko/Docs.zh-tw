---
title: SetAssemblyFile2 方法
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 4f710ef9741869a2b4fd8473ed3ecf379cfcc56d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445594"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="428ae-102">SetAssemblyFile2 方法</span><span class="sxs-lookup"><span data-stu-id="428ae-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="428ae-103">設定新元件的名稱和選項。</span><span class="sxs-lookup"><span data-stu-id="428ae-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="428ae-104">當您產生未系結的模組時，請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="428ae-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428ae-105">語法</span><span class="sxs-lookup"><span data-stu-id="428ae-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="428ae-106">參數</span><span class="sxs-lookup"><span data-stu-id="428ae-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="428ae-107">資訊清單檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="428ae-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="428ae-108">此檔案的[IMetaDataEmit2 介面](../metadata/imetadataemit2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="428ae-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="428ae-109">[AssemblyFlags 列舉](../metadata/assemblyflags-enumeration.md)所表示的選項。</span><span class="sxs-lookup"><span data-stu-id="428ae-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="428ae-110">接收所結構化元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="428ae-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="428ae-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="428ae-111">Return Value</span></span>  
 <span data-ttu-id="428ae-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="428ae-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="428ae-113">需求</span><span class="sxs-lookup"><span data-stu-id="428ae-113">Requirements</span></span>  
 <span data-ttu-id="428ae-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="428ae-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428ae-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="428ae-115">See also</span></span>

- [<span data-ttu-id="428ae-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="428ae-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="428ae-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="428ae-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="428ae-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="428ae-118">ALink API</span></span>](index.md)
