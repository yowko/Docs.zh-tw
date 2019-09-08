---
title: ImportFileEx2 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1c950e9a6e53e04cc0f2e52a140612562b32ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776977"
---
# <a name="importfileex2-method"></a><span data-ttu-id="271a8-102">ImportFileEx2 方法</span><span class="sxs-lookup"><span data-stu-id="271a8-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="271a8-103">匯入元件和解除系結模組。</span><span class="sxs-lookup"><span data-stu-id="271a8-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="271a8-104">這個方法就像[ImportFile 方法](importfile-method.md)，但即使匯入的檔案不存在於磁片上，也會運作。</span><span class="sxs-lookup"><span data-stu-id="271a8-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="271a8-105">語法</span><span class="sxs-lookup"><span data-stu-id="271a8-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="271a8-106">參數</span><span class="sxs-lookup"><span data-stu-id="271a8-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="271a8-107">要匯入之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="271a8-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="271a8-108">目的檔案名的選擇性名稱。</span><span class="sxs-lookup"><span data-stu-id="271a8-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="271a8-109">選擇性的匯入範圍[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="271a8-109">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="271a8-110">若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。</span><span class="sxs-lookup"><span data-stu-id="271a8-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="271a8-111">要傳遞至[OpenScope 方法](../metadata/imetadatadispenser-openscope-method.md)的旗標。</span><span class="sxs-lookup"><span data-stu-id="271a8-111">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="271a8-112">接收元件或檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="271a8-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="271a8-113">接收元件匯入範圍[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="271a8-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="271a8-114">如果檔案不是元件，則可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="271a8-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="271a8-115">接收匯入的檔案和/或範圍數目。</span><span class="sxs-lookup"><span data-stu-id="271a8-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="271a8-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="271a8-116">Return Value</span></span>  
 <span data-ttu-id="271a8-117">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="271a8-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="271a8-118">需求</span><span class="sxs-lookup"><span data-stu-id="271a8-118">Requirements</span></span>  
 <span data-ttu-id="271a8-119">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="271a8-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="271a8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="271a8-120">See also</span></span>

- [<span data-ttu-id="271a8-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="271a8-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="271a8-122">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="271a8-122">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="271a8-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="271a8-123">ALink API</span></span>](index.md)
