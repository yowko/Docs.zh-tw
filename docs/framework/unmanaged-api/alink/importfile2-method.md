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
ms.openlocfilehash: 17f158167d4075783d1aa594fb61cc9e28d30dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446978"
---
# <a name="importfile2-method"></a><span data-ttu-id="5b8d8-102">ImportFile2 方法</span><span class="sxs-lookup"><span data-stu-id="5b8d8-102">ImportFile2 Method</span></span>
<span data-ttu-id="5b8d8-103">匯入元件和解除系結模組。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="5b8d8-104">這個方法就像[ImportFile 方法](importfile-method.md)，但即使匯入的檔案不存在於磁片上，也會運作。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b8d8-105">語法</span><span class="sxs-lookup"><span data-stu-id="5b8d8-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5b8d8-106">參數</span><span class="sxs-lookup"><span data-stu-id="5b8d8-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="5b8d8-107">要匯入之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="5b8d8-108">選擇性的輸出檔案名，可以在檔案連結至元件時用來重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="5b8d8-109">選擇性範圍[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="5b8d8-110">若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="5b8d8-111">接收檔案或元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="5b8d8-112">接收[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="5b8d8-113">如果檔案不是元件，則為 Null。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="5b8d8-114">接收已匯入的檔案和/或範圍的。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b8d8-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="5b8d8-115">Return Value</span></span>  
 <span data-ttu-id="5b8d8-116">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b8d8-117">需求</span><span class="sxs-lookup"><span data-stu-id="5b8d8-117">Requirements</span></span>  
 <span data-ttu-id="5b8d8-118">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="5b8d8-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8d8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b8d8-119">See also</span></span>

- [<span data-ttu-id="5b8d8-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="5b8d8-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5b8d8-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="5b8d8-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5b8d8-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="5b8d8-122">ALink API</span></span>](index.md)
