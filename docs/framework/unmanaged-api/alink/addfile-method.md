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
ms.openlocfilehash: 7ff6bde5009e834bfca156fe4d3ad16da53ded85
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742379"
---
# <a name="addfile-method"></a><span data-ttu-id="4c496-102">AddFile 方法</span><span class="sxs-lookup"><span data-stu-id="4c496-102">AddFile Method</span></span>
<span data-ttu-id="4c496-103">將檔案加入至組件。</span><span class="sxs-lookup"><span data-stu-id="4c496-103">Adds files to the assembly.</span></span> <span data-ttu-id="4c496-104">也可以用來建立未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="4c496-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c496-105">語法</span><span class="sxs-lookup"><span data-stu-id="4c496-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c496-106">參數</span><span class="sxs-lookup"><span data-stu-id="4c496-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4c496-107">要當做引數的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4c496-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="4c496-108">要加入檔案的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="4c496-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4c496-109">COM + FileDef 加上旗標這類`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="4c496-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="4c496-110">`dwFlags` 傳遞給[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="4c496-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="4c496-111">[IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)來發出中繼資料，如有必要的介面。</span><span class="sxs-lookup"><span data-stu-id="4c496-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="4c496-112">若要加入的檔案的唯一識別碼的儲存位置的指標。</span><span class="sxs-lookup"><span data-stu-id="4c496-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c496-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="4c496-113">Return Value</span></span>  
 <span data-ttu-id="4c496-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4c496-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c496-115">需求</span><span class="sxs-lookup"><span data-stu-id="4c496-115">Requirements</span></span>  
 <span data-ttu-id="4c496-116">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="4c496-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c496-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c496-117">See also</span></span>

- [<span data-ttu-id="4c496-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4c496-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="4c496-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4c496-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="4c496-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="4c496-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
