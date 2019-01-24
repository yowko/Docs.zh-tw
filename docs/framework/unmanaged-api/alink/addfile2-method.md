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
ms.openlocfilehash: 078820649543479e65ec35daa6e1cc2876581ddc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693197"
---
# <a name="addfile2-method"></a><span data-ttu-id="57c28-102">AddFile2 方法</span><span class="sxs-lookup"><span data-stu-id="57c28-102">AddFile2 Method</span></span>
<span data-ttu-id="57c28-103">將檔案加入至組件。</span><span class="sxs-lookup"><span data-stu-id="57c28-103">Adds files to the assembly.</span></span> <span data-ttu-id="57c28-104">也可以用來建立未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="57c28-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c28-105">語法</span><span class="sxs-lookup"><span data-stu-id="57c28-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57c28-106">參數</span><span class="sxs-lookup"><span data-stu-id="57c28-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="57c28-107">檔案會加入組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="57c28-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="57c28-108">要加入之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="57c28-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="57c28-109">COM +`FileDef`這類旗標`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="57c28-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="57c28-110">`dwFlags` 傳遞給[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="57c28-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="57c28-111">介面[IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="57c28-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="57c28-112">接收要加入之檔案的 ID。</span><span class="sxs-lookup"><span data-stu-id="57c28-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57c28-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="57c28-113">Return Value</span></span>  
 <span data-ttu-id="57c28-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="57c28-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c28-115">需求</span><span class="sxs-lookup"><span data-stu-id="57c28-115">Requirements</span></span>  
 <span data-ttu-id="57c28-116">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="57c28-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c28-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57c28-117">See also</span></span>
- [<span data-ttu-id="57c28-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="57c28-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="57c28-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="57c28-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="57c28-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="57c28-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
