---
title: EmbedResource 方法
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef7d6272c04c3edab8ef652bcb2759861ff2b982
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129567"
---
# <a name="embedresource-method"></a><span data-ttu-id="eb32c-102">EmbedResource 方法</span><span class="sxs-lookup"><span data-stu-id="eb32c-102">EmbedResource Method</span></span>
<span data-ttu-id="eb32c-103">宣告為內嵌的資源。</span><span class="sxs-lookup"><span data-stu-id="eb32c-103">Declares an embedded resource.</span></span> <span data-ttu-id="eb32c-104">這個方法不會實際內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="eb32c-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb32c-105">語法</span><span class="sxs-lookup"><span data-stu-id="eb32c-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb32c-106">參數</span><span class="sxs-lookup"><span data-stu-id="eb32c-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="eb32c-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="eb32c-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="eb32c-108">語彙基元或組件的檔案識別碼包含資源的檔案。</span><span class="sxs-lookup"><span data-stu-id="eb32c-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="eb32c-109">資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="eb32c-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="eb32c-110">RVA 來自資源的位移。</span><span class="sxs-lookup"><span data-stu-id="eb32c-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="eb32c-111">協助工具加上旗標這類`mrPublic`和`mrPrivate`。</span><span class="sxs-lookup"><span data-stu-id="eb32c-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="eb32c-112">這些旗標可能會傳遞給[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="eb32c-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb32c-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="eb32c-113">Return Value</span></span>  
 <span data-ttu-id="eb32c-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="eb32c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb32c-115">需求</span><span class="sxs-lookup"><span data-stu-id="eb32c-115">Requirements</span></span>  
 <span data-ttu-id="eb32c-116">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="eb32c-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb32c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb32c-117">See also</span></span>

- [<span data-ttu-id="eb32c-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="eb32c-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="eb32c-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="eb32c-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="eb32c-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="eb32c-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
