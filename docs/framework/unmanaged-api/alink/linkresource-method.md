---
title: LinkResource 方法
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 763b7a776007c2ce8dac42c6a5f7f00f6eb58a10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776952"
---
# <a name="linkresource-method"></a><span data-ttu-id="28123-102">LinkResource 方法</span><span class="sxs-lookup"><span data-stu-id="28123-102">LinkResource Method</span></span>
<span data-ttu-id="28123-103">資源中的連結。</span><span class="sxs-lookup"><span data-stu-id="28123-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28123-104">語法</span><span class="sxs-lookup"><span data-stu-id="28123-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="28123-105">參數</span><span class="sxs-lookup"><span data-stu-id="28123-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="28123-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="28123-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="28123-107">檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="28123-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="28123-108">選擇性的新檔案名。</span><span class="sxs-lookup"><span data-stu-id="28123-108">Optional new file name.</span></span> <span data-ttu-id="28123-109">如果不是 Null， `pszFileName`將會複製到 pszNewLocation。</span><span class="sxs-lookup"><span data-stu-id="28123-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="28123-110">資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="28123-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="28123-111">協助工具旗標`mrPublic` ， `mrPrivate`例如和。</span><span class="sxs-lookup"><span data-stu-id="28123-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="28123-112">這個參數可以傳遞至[DefineManifestResource 方法](../metadata/imetadataassemblyemit-definemanifestresource-method.md)。</span><span class="sxs-lookup"><span data-stu-id="28123-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28123-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="28123-113">Return Value</span></span>  
 <span data-ttu-id="28123-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="28123-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28123-115">需求</span><span class="sxs-lookup"><span data-stu-id="28123-115">Requirements</span></span>  
 <span data-ttu-id="28123-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="28123-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28123-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28123-117">See also</span></span>

- [<span data-ttu-id="28123-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="28123-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="28123-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="28123-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="28123-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="28123-120">ALink API</span></span>](index.md)
