---
title: ImportTypes2 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f14822a58f3982d6f9fee1328c10b960657c056f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098464"
---
# <a name="importtypes2-method"></a><span data-ttu-id="960c5-102">ImportTypes2 方法</span><span class="sxs-lookup"><span data-stu-id="960c5-102">ImportTypes2 Method</span></span>
<span data-ttu-id="960c5-103">會起始匯入的類型。</span><span class="sxs-lookup"><span data-stu-id="960c5-103">Initiates the import of types.</span></span> <span data-ttu-id="960c5-104">呼叫這個方法，以開始匯入類型，從透過匯入每個領域[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="960c5-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="960c5-105">語法</span><span class="sxs-lookup"><span data-stu-id="960c5-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="960c5-106">參數</span><span class="sxs-lookup"><span data-stu-id="960c5-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="960c5-107">用來匯入的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="960c5-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="960c5-108">要從中匯入的檔案識別碼。</span><span class="sxs-lookup"><span data-stu-id="960c5-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="960c5-109">要從中匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="960c5-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="960c5-110">指定的範圍內接收類型的列舉值控制代碼。</span><span class="sxs-lookup"><span data-stu-id="960c5-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="960c5-111">選擇性地接收[IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="960c5-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="960c5-112">選擇性地指定範圍內接收類型的計數。</span><span class="sxs-lookup"><span data-stu-id="960c5-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="960c5-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="960c5-113">Return Value</span></span>  
 <span data-ttu-id="960c5-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="960c5-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="960c5-115">需求</span><span class="sxs-lookup"><span data-stu-id="960c5-115">Requirements</span></span>  
 <span data-ttu-id="960c5-116">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="960c5-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="960c5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="960c5-117">See also</span></span>

- [<span data-ttu-id="960c5-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="960c5-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="960c5-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="960c5-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="960c5-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="960c5-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
