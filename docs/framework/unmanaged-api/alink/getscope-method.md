---
title: GetScope Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cb51efc3f431dac4a10cc7582e2b43500ccba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getscope-method1"></a><span data-ttu-id="7b259-102">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="7b259-102">GetScope Method1</span></span>
<span data-ttu-id="7b259-103">取得匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="7b259-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b259-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b259-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b259-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b259-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7b259-106">若要匯入的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7b259-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="7b259-107">要從匯入檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7b259-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="7b259-108">若要匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="7b259-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="7b259-109">接收[IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="7b259-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b259-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="7b259-110">Return Value</span></span>  
 <span data-ttu-id="7b259-111">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="7b259-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b259-112">需求</span><span class="sxs-lookup"><span data-stu-id="7b259-112">Requirements</span></span>  
 <span data-ttu-id="7b259-113">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="7b259-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b259-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7b259-114">See Also</span></span>  
 [<span data-ttu-id="7b259-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="7b259-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7b259-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="7b259-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7b259-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="7b259-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
