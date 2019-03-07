---
title: GetScope 方法
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8de6c745b1d32c3d98f1b54e822ab084f0574b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486195"
---
# <a name="getscope-method"></a><span data-ttu-id="1b49b-102">GetScope 方法</span><span class="sxs-lookup"><span data-stu-id="1b49b-102">GetScope Method</span></span>
<span data-ttu-id="1b49b-103">取得匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="1b49b-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b49b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b49b-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b49b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b49b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1b49b-106">若要匯入的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b49b-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1b49b-107">要從匯入檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b49b-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="1b49b-108">若要匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="1b49b-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="1b49b-109">接收[IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="1b49b-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b49b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b49b-110">Return Value</span></span>  
 <span data-ttu-id="1b49b-111">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1b49b-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b49b-112">需求</span><span class="sxs-lookup"><span data-stu-id="1b49b-112">Requirements</span></span>  
 <span data-ttu-id="1b49b-113">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="1b49b-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b49b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b49b-114">See also</span></span>
- [<span data-ttu-id="1b49b-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="1b49b-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1b49b-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="1b49b-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1b49b-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="1b49b-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
