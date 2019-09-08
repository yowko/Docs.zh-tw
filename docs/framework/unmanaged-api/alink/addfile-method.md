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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1406c68f1f6abff4d140b131f5f630d0fd767e1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787682"
---
# <a name="addfile-method"></a><span data-ttu-id="22ffc-102">AddFile 方法</span><span class="sxs-lookup"><span data-stu-id="22ffc-102">AddFile Method</span></span>
<span data-ttu-id="22ffc-103">將檔案加入至元件。</span><span class="sxs-lookup"><span data-stu-id="22ffc-103">Adds files to the assembly.</span></span> <span data-ttu-id="22ffc-104">也可以用來建立未系結的模組。</span><span class="sxs-lookup"><span data-stu-id="22ffc-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ffc-105">語法</span><span class="sxs-lookup"><span data-stu-id="22ffc-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="22ffc-106">參數</span><span class="sxs-lookup"><span data-stu-id="22ffc-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="22ffc-107">要擴充之元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="22ffc-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="22ffc-108">要新增之檔案的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="22ffc-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="22ffc-109">Com + FileDef 旗標`ffContainsNoMetaData` ， `ffWriteable`例如和。</span><span class="sxs-lookup"><span data-stu-id="22ffc-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="22ffc-110">`dwFlags`會傳遞至[DefineFile 方法](../metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="22ffc-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="22ffc-111">[IMetaDataEmit 介面](../metadata/imetadataemit-interface.md)介面，可用來發出中繼資料（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="22ffc-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="22ffc-112">要儲存所新增檔案之唯一識別碼的位置指標。</span><span class="sxs-lookup"><span data-stu-id="22ffc-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22ffc-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="22ffc-113">Return Value</span></span>  
 <span data-ttu-id="22ffc-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="22ffc-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22ffc-115">需求</span><span class="sxs-lookup"><span data-stu-id="22ffc-115">Requirements</span></span>  
 <span data-ttu-id="22ffc-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="22ffc-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ffc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22ffc-117">See also</span></span>

- [<span data-ttu-id="22ffc-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="22ffc-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="22ffc-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="22ffc-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="22ffc-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="22ffc-120">ALink API</span></span>](index.md)
