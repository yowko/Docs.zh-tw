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
ms.openlocfilehash: af5a200578c34464b5f8d86e568d08d814b46a29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742154"
---
# <a name="embedresource-method"></a><span data-ttu-id="f9c13-102">EmbedResource 方法</span><span class="sxs-lookup"><span data-stu-id="f9c13-102">EmbedResource Method</span></span>
<span data-ttu-id="f9c13-103">宣告為內嵌的資源。</span><span class="sxs-lookup"><span data-stu-id="f9c13-103">Declares an embedded resource.</span></span> <span data-ttu-id="f9c13-104">這個方法不會實際內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="f9c13-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c13-105">語法</span><span class="sxs-lookup"><span data-stu-id="f9c13-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9c13-106">參數</span><span class="sxs-lookup"><span data-stu-id="f9c13-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f9c13-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f9c13-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f9c13-108">語彙基元或組件的檔案識別碼包含資源的檔案。</span><span class="sxs-lookup"><span data-stu-id="f9c13-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="f9c13-109">資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9c13-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="f9c13-110">RVA 來自資源的位移。</span><span class="sxs-lookup"><span data-stu-id="f9c13-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f9c13-111">協助工具加上旗標這類`mrPublic`和`mrPrivate`。</span><span class="sxs-lookup"><span data-stu-id="f9c13-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="f9c13-112">這些旗標可能會傳遞給[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f9c13-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9c13-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="f9c13-113">Return Value</span></span>  
 <span data-ttu-id="f9c13-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f9c13-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c13-115">需求</span><span class="sxs-lookup"><span data-stu-id="f9c13-115">Requirements</span></span>  
 <span data-ttu-id="f9c13-116">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="f9c13-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c13-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9c13-117">See also</span></span>

- [<span data-ttu-id="f9c13-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="f9c13-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f9c13-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="f9c13-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f9c13-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="f9c13-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
