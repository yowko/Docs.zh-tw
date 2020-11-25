---
title: ImportFile 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: f30307884a268008fd4d1a8de31ec5a49b6ab92d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705237"
---
# <a name="importfile-method"></a><span data-ttu-id="db5c2-102">ImportFile 方法</span><span class="sxs-lookup"><span data-stu-id="db5c2-102">ImportFile Method</span></span>

<span data-ttu-id="db5c2-103">匯入元件和未系結的模組。</span><span class="sxs-lookup"><span data-stu-id="db5c2-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db5c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="db5c2-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="db5c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="db5c2-105">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="db5c2-106">要匯入之檔案的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="db5c2-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="db5c2-107">選擇性的輸出檔案名，可在檔案連結至元件時用來重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="db5c2-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="db5c2-108">若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。</span><span class="sxs-lookup"><span data-stu-id="db5c2-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="db5c2-109">標記的指標，其中將儲存唯一的檔案識別碼。</span><span class="sxs-lookup"><span data-stu-id="db5c2-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="db5c2-110">檔案可以是元件或檔案。</span><span class="sxs-lookup"><span data-stu-id="db5c2-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="db5c2-111">接收 [IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)的指標。</span><span class="sxs-lookup"><span data-stu-id="db5c2-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="db5c2-112">如果檔案不是元件，則可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="db5c2-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="db5c2-113">已匯入的檔案和（或）範圍的指標。</span><span class="sxs-lookup"><span data-stu-id="db5c2-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db5c2-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="db5c2-114">Return Value</span></span>  

 <span data-ttu-id="db5c2-115">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="db5c2-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db5c2-116">需求</span><span class="sxs-lookup"><span data-stu-id="db5c2-116">Requirements</span></span>  

 <span data-ttu-id="db5c2-117">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="db5c2-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5c2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db5c2-118">See also</span></span>

- [<span data-ttu-id="db5c2-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="db5c2-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="db5c2-120">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="db5c2-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="db5c2-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="db5c2-121">ALink API</span></span>](index.md)
