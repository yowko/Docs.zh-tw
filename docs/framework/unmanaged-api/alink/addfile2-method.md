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
ms.openlocfilehash: de85d264d709da747fab636f40c99bc0d0752251
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742362"
---
# <a name="addfile2-method"></a><span data-ttu-id="c9e48-102">AddFile2 方法</span><span class="sxs-lookup"><span data-stu-id="c9e48-102">AddFile2 Method</span></span>
<span data-ttu-id="c9e48-103">將檔案加入至組件。</span><span class="sxs-lookup"><span data-stu-id="c9e48-103">Adds files to the assembly.</span></span> <span data-ttu-id="c9e48-104">也可以用來建立未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="c9e48-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e48-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9e48-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9e48-106">參數</span><span class="sxs-lookup"><span data-stu-id="c9e48-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c9e48-107">檔案會加入組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9e48-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="c9e48-108">要加入之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9e48-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c9e48-109">COM +`FileDef`這類旗標`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="c9e48-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="c9e48-110">`dwFlags` 傳遞給[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c9e48-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c9e48-111">介面[IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="c9e48-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c9e48-112">接收要加入之檔案的 ID。</span><span class="sxs-lookup"><span data-stu-id="c9e48-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9e48-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9e48-113">Return Value</span></span>  
 <span data-ttu-id="c9e48-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c9e48-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e48-115">需求</span><span class="sxs-lookup"><span data-stu-id="c9e48-115">Requirements</span></span>  
 <span data-ttu-id="c9e48-116">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="c9e48-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e48-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9e48-117">See also</span></span>

- [<span data-ttu-id="c9e48-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c9e48-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c9e48-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c9e48-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c9e48-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="c9e48-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
