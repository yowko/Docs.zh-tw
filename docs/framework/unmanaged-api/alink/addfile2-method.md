---
title: AddFile2 方法
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: 8dadf9ec8f896b03e4918b21f5153c1b747010fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446672"
---
# <a name="addfile2-method"></a><span data-ttu-id="57228-102">AddFile2 方法</span><span class="sxs-lookup"><span data-stu-id="57228-102">AddFile2 Method</span></span>
<span data-ttu-id="57228-103">將檔案加入至元件。</span><span class="sxs-lookup"><span data-stu-id="57228-103">Adds files to the assembly.</span></span> <span data-ttu-id="57228-104">也可以用來建立未系結的模組。</span><span class="sxs-lookup"><span data-stu-id="57228-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57228-105">語法</span><span class="sxs-lookup"><span data-stu-id="57228-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="57228-106">參數</span><span class="sxs-lookup"><span data-stu-id="57228-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="57228-107">要加入檔案之元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="57228-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="57228-108">要加入的檔案名。</span><span class="sxs-lookup"><span data-stu-id="57228-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="57228-109">COM + `FileDef` 旗標，例如 `ffContainsNoMetaData` 和 `ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="57228-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="57228-110">`dwFlags` 會傳遞至[DefineFile 方法](../metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="57228-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="57228-111">介面至[IMetaDataEmit2 介面](../metadata/imetadataemit2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="57228-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="57228-112">接收要加入之檔案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="57228-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57228-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="57228-113">Return Value</span></span>  
 <span data-ttu-id="57228-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="57228-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57228-115">需求</span><span class="sxs-lookup"><span data-stu-id="57228-115">Requirements</span></span>  
 <span data-ttu-id="57228-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="57228-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57228-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57228-117">See also</span></span>

- [<span data-ttu-id="57228-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="57228-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="57228-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="57228-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="57228-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="57228-120">ALink API</span></span>](index.md)
