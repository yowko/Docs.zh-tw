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
ms.openlocfilehash: 4f2f13976dfd4e5601bf8b54bed7b851884fbb9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690443"
---
# <a name="linkresource-method"></a><span data-ttu-id="b1011-102">LinkResource 方法</span><span class="sxs-lookup"><span data-stu-id="b1011-102">LinkResource Method</span></span>

<span data-ttu-id="b1011-103">資源中的連結。</span><span class="sxs-lookup"><span data-stu-id="b1011-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1011-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1011-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1011-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1011-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="b1011-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b1011-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="b1011-107">檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1011-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="b1011-108">選用的新檔案名。</span><span class="sxs-lookup"><span data-stu-id="b1011-108">Optional new file name.</span></span> <span data-ttu-id="b1011-109">如果非 Null， `pszFileName` 將會複製到 pszNewLocation。</span><span class="sxs-lookup"><span data-stu-id="b1011-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="b1011-110">資源名稱。</span><span class="sxs-lookup"><span data-stu-id="b1011-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b1011-111">協助工具旗標 `mrPublic` ，例如和 `mrPrivate` 。</span><span class="sxs-lookup"><span data-stu-id="b1011-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="b1011-112">這個參數可以傳遞給 [DefineManifestResource 方法](../metadata/imetadataassemblyemit-definemanifestresource-method.md)。</span><span class="sxs-lookup"><span data-stu-id="b1011-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1011-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="b1011-113">Return Value</span></span>  

 <span data-ttu-id="b1011-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="b1011-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1011-115">需求</span><span class="sxs-lookup"><span data-stu-id="b1011-115">Requirements</span></span>  

 <span data-ttu-id="b1011-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="b1011-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1011-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1011-117">See also</span></span>

- [<span data-ttu-id="b1011-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="b1011-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b1011-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="b1011-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b1011-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="b1011-120">ALink API</span></span>](index.md)
