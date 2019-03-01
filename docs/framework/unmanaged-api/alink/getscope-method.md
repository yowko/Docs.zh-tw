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
ms.openlocfilehash: c5798fc488cf4453b6abcf00a7169b1ec0b529ec
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965367"
---
# <a name="getscope-method"></a><span data-ttu-id="83496-102">GetScope 方法</span><span class="sxs-lookup"><span data-stu-id="83496-102">GetScope Method</span></span>
<span data-ttu-id="83496-103">取得匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="83496-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83496-104">語法</span><span class="sxs-lookup"><span data-stu-id="83496-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83496-105">參數</span><span class="sxs-lookup"><span data-stu-id="83496-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="83496-106">若要匯入的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="83496-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="83496-107">要從匯入檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="83496-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="83496-108">若要匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="83496-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="83496-109">接收[IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="83496-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83496-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="83496-110">Return Value</span></span>  
 <span data-ttu-id="83496-111">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="83496-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83496-112">需求</span><span class="sxs-lookup"><span data-stu-id="83496-112">Requirements</span></span>  
 <span data-ttu-id="83496-113">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="83496-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83496-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83496-114">See also</span></span>
- [<span data-ttu-id="83496-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="83496-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="83496-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="83496-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="83496-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="83496-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
