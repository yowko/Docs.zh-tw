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
ms.openlocfilehash: a03fc24e5ef932d13c0d195f53c703cdd3ff45ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776933"
---
# <a name="importfile2-method"></a><span data-ttu-id="a9bb0-102">ImportFile2 方法</span><span class="sxs-lookup"><span data-stu-id="a9bb0-102">ImportFile2 Method</span></span>
<span data-ttu-id="a9bb0-103">匯入元件和解除系結模組。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="a9bb0-104">這個方法就像[ImportFile 方法](importfile-method.md)，但即使匯入的檔案不存在於磁片上，也會運作。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9bb0-105">語法</span><span class="sxs-lookup"><span data-stu-id="a9bb0-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="a9bb0-106">參數</span><span class="sxs-lookup"><span data-stu-id="a9bb0-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="a9bb0-107">要匯入之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="a9bb0-108">選擇性的輸出檔案名，可以在檔案連結至元件時用來重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="a9bb0-109">選擇性範圍[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="a9bb0-110">若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="a9bb0-111">接收檔案或元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="a9bb0-112">接收[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="a9bb0-113">如果檔案不是元件，則為 Null。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="a9bb0-114">接收已匯入的檔案和/或範圍的。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9bb0-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="a9bb0-115">Return Value</span></span>  
 <span data-ttu-id="a9bb0-116">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9bb0-117">需求</span><span class="sxs-lookup"><span data-stu-id="a9bb0-117">Requirements</span></span>  
 <span data-ttu-id="a9bb0-118">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bb0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9bb0-119">See also</span></span>

- [<span data-ttu-id="a9bb0-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="a9bb0-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a9bb0-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="a9bb0-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a9bb0-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="a9bb0-122">ALink API</span></span>](index.md)
