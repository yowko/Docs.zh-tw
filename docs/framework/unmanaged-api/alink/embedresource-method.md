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
ms.openlocfilehash: 5f6140e5f85a7ee21773c96a5abdccadaddab92e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777454"
---
# <a name="embedresource-method"></a><span data-ttu-id="3e39a-102">EmbedResource 方法</span><span class="sxs-lookup"><span data-stu-id="3e39a-102">EmbedResource Method</span></span>
<span data-ttu-id="3e39a-103">宣告內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="3e39a-103">Declares an embedded resource.</span></span> <span data-ttu-id="3e39a-104">這個方法不會實際內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="3e39a-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e39a-105">語法</span><span class="sxs-lookup"><span data-stu-id="3e39a-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e39a-106">參數</span><span class="sxs-lookup"><span data-stu-id="3e39a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3e39a-107">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3e39a-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3e39a-108">包含資源之檔案的檔案 token 或元件識別碼。</span><span class="sxs-lookup"><span data-stu-id="3e39a-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="3e39a-109">資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e39a-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="3e39a-110">來自 RVA 的資源位移。</span><span class="sxs-lookup"><span data-stu-id="3e39a-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3e39a-111">協助工具旗標`mrPublic` ， `mrPrivate`例如和。</span><span class="sxs-lookup"><span data-stu-id="3e39a-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="3e39a-112">這些旗標可能會傳遞至[DefineExportedType 方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3e39a-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e39a-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="3e39a-113">Return Value</span></span>  
 <span data-ttu-id="3e39a-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="3e39a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e39a-115">需求</span><span class="sxs-lookup"><span data-stu-id="3e39a-115">Requirements</span></span>  
 <span data-ttu-id="3e39a-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="3e39a-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e39a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e39a-117">See also</span></span>

- [<span data-ttu-id="3e39a-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="3e39a-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3e39a-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="3e39a-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3e39a-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="3e39a-120">ALink API</span></span>](index.md)
