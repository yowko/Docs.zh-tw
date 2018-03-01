---
title: AddImport Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d8827821deaeda311a42855737ecf53ab635a02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="addimport-method1"></a><span data-ttu-id="e2f74-102">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="e2f74-102">AddImport Method1</span></span>
<span data-ttu-id="e2f74-103">將組件匯入。</span><span class="sxs-lookup"><span data-stu-id="e2f74-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f74-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2f74-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2f74-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2f74-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e2f74-106">要當做引數的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="e2f74-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="e2f74-107">唯一識別碼，從擷取[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，要匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="e2f74-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e2f74-108">COM + FileDef 旗標，例如`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="e2f74-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="e2f74-109">`dwFlags`傳遞至[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e2f74-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="e2f74-110">接收所產生的檔案 ID 的語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="e2f74-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2f74-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="e2f74-111">Return Value</span></span>  
 <span data-ttu-id="e2f74-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e2f74-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2f74-113">需求</span><span class="sxs-lookup"><span data-stu-id="e2f74-113">Requirements</span></span>  
 <span data-ttu-id="e2f74-114">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="e2f74-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f74-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2f74-115">See Also</span></span>  
 [<span data-ttu-id="e2f74-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="e2f74-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e2f74-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="e2f74-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e2f74-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="e2f74-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
