---
title: ImportFile2 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88006703ba4a491ae458868a1431be618d37252a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471195"
---
# <a name="importfile2-method"></a><span data-ttu-id="9b9a5-102">ImportFile2 方法</span><span class="sxs-lookup"><span data-stu-id="9b9a5-102">ImportFile2 Method</span></span>
<span data-ttu-id="9b9a5-103">匯入組件和未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="9b9a5-104">這個方法就像是[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，但即使正在匯入的檔案不存在磁碟上的運作方式。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b9a5-105">語法</span><span class="sxs-lookup"><span data-stu-id="9b9a5-105">Syntax</span></span>  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b9a5-106">參數</span><span class="sxs-lookup"><span data-stu-id="9b9a5-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="9b9a5-107">要匯入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="9b9a5-108">可用來重新命名檔案，因為它連結至組件的選擇性的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="9b9a5-109">選擇性的範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="9b9a5-110">如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="9b9a5-111">接收的檔案或組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="9b9a5-112">接收[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="9b9a5-113">如果檔案不是組件，則為 NULL。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="9b9a5-114">會接收找到的檔案和/或匯入的範圍。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b9a5-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="9b9a5-115">Return Value</span></span>  
 <span data-ttu-id="9b9a5-116">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b9a5-117">需求</span><span class="sxs-lookup"><span data-stu-id="9b9a5-117">Requirements</span></span>  
 <span data-ttu-id="9b9a5-118">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="9b9a5-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b9a5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b9a5-119">See also</span></span>
- [<span data-ttu-id="9b9a5-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="9b9a5-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9b9a5-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="9b9a5-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9b9a5-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="9b9a5-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
