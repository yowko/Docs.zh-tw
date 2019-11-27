---
title: ImportFileEx 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
ms.openlocfilehash: bee7db61beb9ed8c00cf584924be690a67d92eac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446959"
---
# <a name="importfileex-method"></a><span data-ttu-id="030c5-102">ImportFileEx 方法</span><span class="sxs-lookup"><span data-stu-id="030c5-102">ImportFileEx Method</span></span>
<span data-ttu-id="030c5-103">匯入指定的元件或解除系結模組。</span><span class="sxs-lookup"><span data-stu-id="030c5-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="030c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="030c5-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="030c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="030c5-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="030c5-106">要匯入之檔案的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="030c5-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="030c5-107">目的檔案名的選擇性名稱。</span><span class="sxs-lookup"><span data-stu-id="030c5-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="030c5-108">若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。</span><span class="sxs-lookup"><span data-stu-id="030c5-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="030c5-109">要傳遞至[OpenScope 方法](../metadata/imetadatadispenser-openscope-method.md)的旗標。</span><span class="sxs-lookup"><span data-stu-id="030c5-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="030c5-110">接收正在匯入之檔案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="030c5-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="030c5-111">接收元件匯入範圍[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="030c5-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="030c5-112">如果檔案不是元件，則會設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="030c5-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="030c5-113">接收匯入的檔案和/或範圍的計數。</span><span class="sxs-lookup"><span data-stu-id="030c5-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="030c5-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="030c5-114">Return Value</span></span>  
 <span data-ttu-id="030c5-115">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="030c5-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="030c5-116">需求</span><span class="sxs-lookup"><span data-stu-id="030c5-116">Requirements</span></span>  
 <span data-ttu-id="030c5-117">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="030c5-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030c5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="030c5-118">See also</span></span>

- [<span data-ttu-id="030c5-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="030c5-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="030c5-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="030c5-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="030c5-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="030c5-121">ALink API</span></span>](index.md)
