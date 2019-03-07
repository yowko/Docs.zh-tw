---
title: AddImport 方法
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 261d80caa43ec478d3a3a33acdebcc1bfcfde8cf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500703"
---
# <a name="addimport-method"></a><span data-ttu-id="b2995-102">AddImport 方法</span><span class="sxs-lookup"><span data-stu-id="b2995-102">AddImport Method</span></span>
<span data-ttu-id="b2995-103">將組件匯入。</span><span class="sxs-lookup"><span data-stu-id="b2995-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2995-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2995-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2995-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2995-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b2995-106">要當做引數的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="b2995-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="b2995-107">唯一的識別碼，擷取自[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，要匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="b2995-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b2995-108">COM + FileDef 加上旗標這類`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="b2995-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="b2995-109">`dwFlags` 傳遞給[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="b2995-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="b2995-110">接收所產生的檔案識別碼的語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="b2995-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2995-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="b2995-111">Return Value</span></span>  
 <span data-ttu-id="b2995-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="b2995-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2995-113">需求</span><span class="sxs-lookup"><span data-stu-id="b2995-113">Requirements</span></span>  
 <span data-ttu-id="b2995-114">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="b2995-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2995-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2995-115">See also</span></span>
- [<span data-ttu-id="b2995-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="b2995-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="b2995-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="b2995-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="b2995-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="b2995-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
