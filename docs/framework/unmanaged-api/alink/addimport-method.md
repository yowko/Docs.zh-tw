---
title: AddImport Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddImport
- IALink.AddImport
api_location: alink.dll
api_type: COM
f1_keywords: AddImport
helpviewer_keywords: AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cd0e55cab6f0fdb7f971d7cf06e5703340e32307
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="addimport-method1"></a><span data-ttu-id="7edcb-102">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="7edcb-102">AddImport Method1</span></span>
<span data-ttu-id="7edcb-103">將組件匯入。</span><span class="sxs-lookup"><span data-stu-id="7edcb-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7edcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="7edcb-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7edcb-105">參數</span><span class="sxs-lookup"><span data-stu-id="7edcb-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7edcb-106">要當做引數的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7edcb-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="7edcb-107">唯一識別碼，從擷取[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，要匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="7edcb-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7edcb-108">COM + FileDef 旗標，例如`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="7edcb-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="7edcb-109">`dwFlags`傳遞至[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="7edcb-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="7edcb-110">接收所產生的檔案 ID 的語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="7edcb-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7edcb-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="7edcb-111">Return Value</span></span>  
 <span data-ttu-id="7edcb-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="7edcb-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7edcb-113">需求</span><span class="sxs-lookup"><span data-stu-id="7edcb-113">Requirements</span></span>  
 <span data-ttu-id="7edcb-114">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="7edcb-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7edcb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7edcb-115">See Also</span></span>  
 [<span data-ttu-id="7edcb-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="7edcb-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7edcb-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="7edcb-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7edcb-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="7edcb-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
