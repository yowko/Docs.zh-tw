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
ms.openlocfilehash: 7a651be40773607e0db215eadf884ed642e6e3b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126928"
---
# <a name="addfile2-method"></a><span data-ttu-id="c7d9b-102">AddFile2 方法</span><span class="sxs-lookup"><span data-stu-id="c7d9b-102">AddFile2 Method</span></span>
<span data-ttu-id="c7d9b-103">將檔案加入至組件。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-103">Adds files to the assembly.</span></span> <span data-ttu-id="c7d9b-104">也可以用來建立未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d9b-105">語法</span><span class="sxs-lookup"><span data-stu-id="c7d9b-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7d9b-106">參數</span><span class="sxs-lookup"><span data-stu-id="c7d9b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c7d9b-107">檔案會加入組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="c7d9b-108">要加入之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c7d9b-109">COM +`FileDef`這類旗標`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> `dwFlags` <span data-ttu-id="c7d9b-110">傳遞給[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-110">is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c7d9b-111">介面[IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c7d9b-112">接收要加入之檔案的 ID。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7d9b-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="c7d9b-113">Return Value</span></span>  
 <span data-ttu-id="c7d9b-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d9b-115">需求</span><span class="sxs-lookup"><span data-stu-id="c7d9b-115">Requirements</span></span>  
 <span data-ttu-id="c7d9b-116">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="c7d9b-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d9b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7d9b-117">See also</span></span>

- [<span data-ttu-id="c7d9b-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c7d9b-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c7d9b-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c7d9b-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c7d9b-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="c7d9b-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
