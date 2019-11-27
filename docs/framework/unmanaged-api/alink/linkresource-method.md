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
ms.openlocfilehash: 9e91d990a8f23335248043c59eb210e8c4155e3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445626"
---
# <a name="linkresource-method"></a><span data-ttu-id="87ee1-102">LinkResource 方法</span><span class="sxs-lookup"><span data-stu-id="87ee1-102">LinkResource Method</span></span>
<span data-ttu-id="87ee1-103">資源中的連結。</span><span class="sxs-lookup"><span data-stu-id="87ee1-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ee1-104">語法</span><span class="sxs-lookup"><span data-stu-id="87ee1-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="87ee1-105">參數</span><span class="sxs-lookup"><span data-stu-id="87ee1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="87ee1-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="87ee1-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="87ee1-107">檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="87ee1-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="87ee1-108">選擇性的新檔案名。</span><span class="sxs-lookup"><span data-stu-id="87ee1-108">Optional new file name.</span></span> <span data-ttu-id="87ee1-109">如果不是 Null，`pszFileName` 會複製到 pszNewLocation。</span><span class="sxs-lookup"><span data-stu-id="87ee1-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="87ee1-110">資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="87ee1-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="87ee1-111">協助工具旗標，例如 `mrPublic` 和 `mrPrivate`。</span><span class="sxs-lookup"><span data-stu-id="87ee1-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="87ee1-112">這個參數可以傳遞至[DefineManifestResource 方法](../metadata/imetadataassemblyemit-definemanifestresource-method.md)。</span><span class="sxs-lookup"><span data-stu-id="87ee1-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87ee1-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="87ee1-113">Return Value</span></span>  
 <span data-ttu-id="87ee1-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="87ee1-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ee1-115">需求</span><span class="sxs-lookup"><span data-stu-id="87ee1-115">Requirements</span></span>  
 <span data-ttu-id="87ee1-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="87ee1-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ee1-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="87ee1-117">See also</span></span>

- [<span data-ttu-id="87ee1-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="87ee1-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="87ee1-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="87ee1-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="87ee1-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="87ee1-120">ALink API</span></span>](index.md)
