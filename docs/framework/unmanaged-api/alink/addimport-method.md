---
title: AddImport Method1
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
ms.openlocfilehash: 98fefc0240f6496a3e7bfb491e27a57e98cfea1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404062"
---
# <a name="addimport-method1"></a><span data-ttu-id="760d6-102">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="760d6-102">AddImport Method1</span></span>
<span data-ttu-id="760d6-103">將組件匯入。</span><span class="sxs-lookup"><span data-stu-id="760d6-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="760d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="760d6-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="760d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="760d6-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="760d6-106">要當做引數的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="760d6-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="760d6-107">唯一識別碼，從擷取[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，要匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="760d6-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="760d6-108">COM + FileDef 旗標，例如`ffContainsNoMetaData`和`ffWriteable`。</span><span class="sxs-lookup"><span data-stu-id="760d6-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="760d6-109">`dwFlags` 傳遞至[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="760d6-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="760d6-110">接收所產生的檔案 ID 的語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="760d6-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="760d6-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="760d6-111">Return Value</span></span>  
 <span data-ttu-id="760d6-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="760d6-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="760d6-113">需求</span><span class="sxs-lookup"><span data-stu-id="760d6-113">Requirements</span></span>  
 <span data-ttu-id="760d6-114">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="760d6-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="760d6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="760d6-115">See Also</span></span>  
 [<span data-ttu-id="760d6-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="760d6-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="760d6-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="760d6-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="760d6-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="760d6-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
