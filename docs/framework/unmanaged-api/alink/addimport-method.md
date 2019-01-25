---
title: AddImport 方法 1
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
ms.openlocfilehash: d2daed0450e04137621788e830bbedb467bd57c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706335"
---
# <a name="addimport-method1"></a><span data-ttu-id="56466-102">AddImport 方法 1</span><span class="sxs-lookup"><span data-stu-id="56466-102">AddImport Method1</span></span>
<span data-ttu-id="56466-103">將組件匯入。</span><span class="sxs-lookup"><span data-stu-id="56466-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56466-104">語法</span><span class="sxs-lookup"><span data-stu-id="56466-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56466-105">參數</span><span class="sxs-lookup"><span data-stu-id="56466-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="56466-106">要當做引數的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="56466-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="56466-107">唯一的識別碼，擷取自[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，要匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="56466-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="56466-108">COM + FileDef 加上旗標這類`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="56466-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="56466-109">`dwFlags` 傳遞給[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="56466-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="56466-110">接收所產生的檔案識別碼的語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="56466-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56466-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="56466-111">Return Value</span></span>  
 <span data-ttu-id="56466-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="56466-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56466-113">需求</span><span class="sxs-lookup"><span data-stu-id="56466-113">Requirements</span></span>  
 <span data-ttu-id="56466-114">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="56466-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56466-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56466-115">See also</span></span>
- [<span data-ttu-id="56466-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="56466-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="56466-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="56466-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="56466-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="56466-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
