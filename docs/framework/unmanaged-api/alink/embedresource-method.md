---
title: "EmbedResource 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmbedResource
- EmbedResource
api_location: alink.dll
api_type: COM
f1_keywords: EmbedResource
helpviewer_keywords: EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 815e4b6abbb56b0998a12c096f0ba7cb678778ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="embedresource-method"></a><span data-ttu-id="62e8d-102">EmbedResource 方法</span><span class="sxs-lookup"><span data-stu-id="62e8d-102">EmbedResource Method</span></span>
<span data-ttu-id="62e8d-103">宣告為內嵌的資源。</span><span class="sxs-lookup"><span data-stu-id="62e8d-103">Declares an embedded resource.</span></span> <span data-ttu-id="62e8d-104">這個方法不會實際內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="62e8d-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e8d-105">語法</span><span class="sxs-lookup"><span data-stu-id="62e8d-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62e8d-106">參數</span><span class="sxs-lookup"><span data-stu-id="62e8d-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="62e8d-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="62e8d-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="62e8d-108">語彙基元或組件的檔案識別碼包含資源的檔案。</span><span class="sxs-lookup"><span data-stu-id="62e8d-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="62e8d-109">資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="62e8d-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="62e8d-110">位移 RVA 的資源。</span><span class="sxs-lookup"><span data-stu-id="62e8d-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="62e8d-111">存取範圍旗標，例如`mrPublic`和`mrPrivate`。</span><span class="sxs-lookup"><span data-stu-id="62e8d-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="62e8d-112">這些旗標可能會傳遞至[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="62e8d-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62e8d-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="62e8d-113">Return Value</span></span>  
 <span data-ttu-id="62e8d-114">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="62e8d-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e8d-115">需求</span><span class="sxs-lookup"><span data-stu-id="62e8d-115">Requirements</span></span>  
 <span data-ttu-id="62e8d-116">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="62e8d-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e8d-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="62e8d-117">See Also</span></span>  
 [<span data-ttu-id="62e8d-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="62e8d-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="62e8d-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="62e8d-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="62e8d-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="62e8d-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
