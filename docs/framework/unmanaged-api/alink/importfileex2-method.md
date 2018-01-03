---
title: "ImportFileEx2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx2
helpviewer_keywords: ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78ed173e795b875a171edd8ce49b11df49570827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="importfileex2-method"></a><span data-ttu-id="1eb77-102">ImportFileEx2 方法</span><span class="sxs-lookup"><span data-stu-id="1eb77-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="1eb77-103">匯入組件和未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="1eb77-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="1eb77-104">這個方法就像[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，但即使正在匯入的檔案不存在磁碟上的運作方式。</span><span class="sxs-lookup"><span data-stu-id="1eb77-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eb77-105">語法</span><span class="sxs-lookup"><span data-stu-id="1eb77-105">Syntax</span></span>  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1eb77-106">參數</span><span class="sxs-lookup"><span data-stu-id="1eb77-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="1eb77-107">要匯入檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="1eb77-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="1eb77-108">選用的目標檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1eb77-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="1eb77-109">選擇性的匯入範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="1eb77-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="1eb77-110">如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。</span><span class="sxs-lookup"><span data-stu-id="1eb77-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="1eb77-111">旗標，以傳送到[OpenScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb77-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="1eb77-112">接收的組件或檔案的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="1eb77-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="1eb77-113">接收的組件匯入範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="1eb77-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="1eb77-114">如果檔案不是組件時，就可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="1eb77-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="1eb77-115">接收檔案及/或匯入的範圍的數目。</span><span class="sxs-lookup"><span data-stu-id="1eb77-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1eb77-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="1eb77-116">Return Value</span></span>  
 <span data-ttu-id="1eb77-117">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1eb77-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eb77-118">需求</span><span class="sxs-lookup"><span data-stu-id="1eb77-118">Requirements</span></span>  
 <span data-ttu-id="1eb77-119">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="1eb77-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb77-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="1eb77-120">See Also</span></span>  
 [<span data-ttu-id="1eb77-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="1eb77-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1eb77-122">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="1eb77-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1eb77-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="1eb77-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
