---
title: AddFile 方法
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
ms.openlocfilehash: 4dd104805d547613315335bc9c95b5c60a9cab14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446678"
---
# <a name="addfile-method"></a><span data-ttu-id="ae7c9-102">AddFile 方法</span><span class="sxs-lookup"><span data-stu-id="ae7c9-102">AddFile Method</span></span>
<span data-ttu-id="ae7c9-103">Adds files to the assembly.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-103">Adds files to the assembly.</span></span> <span data-ttu-id="ae7c9-104">Can also be used to create unbound modules.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7c9-105">語法</span><span class="sxs-lookup"><span data-stu-id="ae7c9-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae7c9-106">參數</span><span class="sxs-lookup"><span data-stu-id="ae7c9-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ae7c9-107">Unique ID of the assembly to be augmented.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="ae7c9-108">Fully qualified name of file to be added.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ae7c9-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="ae7c9-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae7c9-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="ae7c9-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="ae7c9-112">Pointer to where the unique ID of the added file will be stored.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae7c9-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae7c9-113">Return Value</span></span>  
 <span data-ttu-id="ae7c9-114">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae7c9-115">需求</span><span class="sxs-lookup"><span data-stu-id="ae7c9-115">Requirements</span></span>  
 <span data-ttu-id="ae7c9-116">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="ae7c9-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7c9-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="ae7c9-117">See also</span></span>

- [<span data-ttu-id="ae7c9-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ae7c9-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ae7c9-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ae7c9-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ae7c9-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="ae7c9-120">ALink API</span></span>](index.md)
