---
title: GetScope Method1
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
ms.openlocfilehash: e2746073fbc6adfd7090aa9b3cc38e46c4411744
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400181"
---
# <a name="getscope-method1"></a><span data-ttu-id="1fa6b-102">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="1fa6b-102">GetScope Method1</span></span>
<span data-ttu-id="1fa6b-103">取得匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="1fa6b-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1fa6b-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fa6b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1fa6b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1fa6b-106">若要匯入的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1fa6b-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1fa6b-107">要從匯入檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1fa6b-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="1fa6b-108">若要匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="1fa6b-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="1fa6b-109">接收[IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="1fa6b-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fa6b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="1fa6b-110">Return Value</span></span>  
 <span data-ttu-id="1fa6b-111">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1fa6b-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fa6b-112">需求</span><span class="sxs-lookup"><span data-stu-id="1fa6b-112">Requirements</span></span>  
 <span data-ttu-id="1fa6b-113">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="1fa6b-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa6b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fa6b-114">See Also</span></span>  
 [<span data-ttu-id="1fa6b-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="1fa6b-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1fa6b-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="1fa6b-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1fa6b-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="1fa6b-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
