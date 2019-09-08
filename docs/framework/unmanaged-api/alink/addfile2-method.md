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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3a6892dbed172c0be3b036014d393657dbc8593
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777515"
---
# <a name="addfile2-method"></a><span data-ttu-id="2a41c-102">AddFile2 方法</span><span class="sxs-lookup"><span data-stu-id="2a41c-102">AddFile2 Method</span></span>
<span data-ttu-id="2a41c-103">將檔案加入至元件。</span><span class="sxs-lookup"><span data-stu-id="2a41c-103">Adds files to the assembly.</span></span> <span data-ttu-id="2a41c-104">也可以用來建立未系結的模組。</span><span class="sxs-lookup"><span data-stu-id="2a41c-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a41c-105">語法</span><span class="sxs-lookup"><span data-stu-id="2a41c-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a41c-106">參數</span><span class="sxs-lookup"><span data-stu-id="2a41c-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2a41c-107">要加入檔案之元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2a41c-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="2a41c-108">要加入的檔案名。</span><span class="sxs-lookup"><span data-stu-id="2a41c-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2a41c-109">Com `FileDef` + 旗標`ffContainsNoMetaData` ， `ffWriteable`例如和。</span><span class="sxs-lookup"><span data-stu-id="2a41c-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="2a41c-110">`dwFlags`會傳遞至[DefineFile 方法](../metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2a41c-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="2a41c-111">介面至[IMetaDataEmit2 介面](../metadata/imetadataemit2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="2a41c-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="2a41c-112">接收要加入之檔案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2a41c-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a41c-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="2a41c-113">Return Value</span></span>  
 <span data-ttu-id="2a41c-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="2a41c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a41c-115">需求</span><span class="sxs-lookup"><span data-stu-id="2a41c-115">Requirements</span></span>  
 <span data-ttu-id="2a41c-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="2a41c-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a41c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a41c-117">See also</span></span>

- [<span data-ttu-id="2a41c-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="2a41c-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2a41c-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="2a41c-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2a41c-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="2a41c-120">ALink API</span></span>](index.md)
