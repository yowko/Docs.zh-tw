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
ms.openlocfilehash: 61bc7783823408164ae2b073e097a0e85e193be6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401238"
---
# <a name="importfile2-method"></a><span data-ttu-id="56638-102">ImportFile2 方法</span><span class="sxs-lookup"><span data-stu-id="56638-102">ImportFile2 Method</span></span>
<span data-ttu-id="56638-103">匯入組件和未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="56638-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="56638-104">這個方法就像[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，但即使正在匯入的檔案不存在磁碟上的運作方式。</span><span class="sxs-lookup"><span data-stu-id="56638-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56638-105">語法</span><span class="sxs-lookup"><span data-stu-id="56638-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="56638-106">參數</span><span class="sxs-lookup"><span data-stu-id="56638-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="56638-107">要匯入檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="56638-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="56638-108">可用來重新命名檔案，因為它會連結至組件的選擇性的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="56638-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="56638-109">選擇性的範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="56638-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="56638-110">如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。</span><span class="sxs-lookup"><span data-stu-id="56638-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="56638-111">接收檔案或組件的 ID。</span><span class="sxs-lookup"><span data-stu-id="56638-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="56638-112">接收[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="56638-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="56638-113">如果檔案不是組件，則為 NULL。</span><span class="sxs-lookup"><span data-stu-id="56638-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="56638-114">會接收找到檔案及/或匯入的範圍。</span><span class="sxs-lookup"><span data-stu-id="56638-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56638-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="56638-115">Return Value</span></span>  
 <span data-ttu-id="56638-116">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="56638-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56638-117">需求</span><span class="sxs-lookup"><span data-stu-id="56638-117">Requirements</span></span>  
 <span data-ttu-id="56638-118">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="56638-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56638-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56638-119">See Also</span></span>  
 [<span data-ttu-id="56638-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="56638-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="56638-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="56638-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="56638-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="56638-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
