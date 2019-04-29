---
title: ImportTypes 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 622e57aedf6c49e95dc2d7e40ba598361b3e6a26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753448"
---
# <a name="importtypes-method"></a><span data-ttu-id="179ca-102">ImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="179ca-102">ImportTypes Method</span></span>
<span data-ttu-id="179ca-103">匯入的類型，從透過匯入每個範圍的起始[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="179ca-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="179ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="179ca-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="179ca-105">參數</span><span class="sxs-lookup"><span data-stu-id="179ca-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="179ca-106">若要匯入的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="179ca-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="179ca-107">若要從匯入的檔案識別碼。</span><span class="sxs-lookup"><span data-stu-id="179ca-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="179ca-108">若要匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="179ca-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="179ca-109">在這個範圍中，接收列舉值類型的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="179ca-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="179ca-110">選擇性地接收[IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="179ca-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="179ca-111">選擇性地指定範圍內接收類型的計數。</span><span class="sxs-lookup"><span data-stu-id="179ca-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="179ca-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="179ca-112">Return Value</span></span>  
 <span data-ttu-id="179ca-113">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="179ca-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="179ca-114">需求</span><span class="sxs-lookup"><span data-stu-id="179ca-114">Requirements</span></span>  
 <span data-ttu-id="179ca-115">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="179ca-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="179ca-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="179ca-116">See also</span></span>

- [<span data-ttu-id="179ca-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="179ca-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="179ca-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="179ca-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="179ca-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="179ca-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
