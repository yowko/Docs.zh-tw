---
title: GetScope2 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3c11eeeb4eece495a7ccbe51c7e04d077e497ce
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494567"
---
# <a name="getscope2-method"></a><span data-ttu-id="4b5ab-102">GetScope2 方法</span><span class="sxs-lookup"><span data-stu-id="4b5ab-102">GetScope2 Method</span></span>
<span data-ttu-id="4b5ab-103">取得匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b5ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b5ab-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="4b5ab-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b5ab-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4b5ab-106">目標組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4b5ab-107">要從中匯入的檔案識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="4b5ab-108">若要匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="4b5ab-109">接收指標[IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)指定範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b5ab-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b5ab-110">Return Value</span></span>  
 <span data-ttu-id="4b5ab-111">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b5ab-112">需求</span><span class="sxs-lookup"><span data-stu-id="4b5ab-112">Requirements</span></span>  
 <span data-ttu-id="4b5ab-113">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5ab-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b5ab-114">See also</span></span>
- [<span data-ttu-id="4b5ab-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4b5ab-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="4b5ab-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4b5ab-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="4b5ab-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="4b5ab-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
