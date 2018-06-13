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
ms.openlocfilehash: 4f75ebc3a40bddbaf2347b9ef559139888f83900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401104"
---
# <a name="linkresource-method"></a><span data-ttu-id="819a7-102">LinkResource 方法</span><span class="sxs-lookup"><span data-stu-id="819a7-102">LinkResource Method</span></span>
<span data-ttu-id="819a7-103">在資源中的連結。</span><span class="sxs-lookup"><span data-stu-id="819a7-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="819a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="819a7-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="819a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="819a7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="819a7-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="819a7-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="819a7-107">檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="819a7-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="819a7-108">選擇性的新檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="819a7-108">Optional new file name.</span></span> <span data-ttu-id="819a7-109">如果不是 NULL，`pszFileName`會複製到 pszNewLocation。</span><span class="sxs-lookup"><span data-stu-id="819a7-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="819a7-110">資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="819a7-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="819a7-111">存取範圍旗標，例如`mrPublic`和`mrPrivate`。</span><span class="sxs-lookup"><span data-stu-id="819a7-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="819a7-112">此參數可能會傳遞至[DefineManifestResource 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)。</span><span class="sxs-lookup"><span data-stu-id="819a7-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="819a7-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="819a7-113">Return Value</span></span>  
 <span data-ttu-id="819a7-114">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="819a7-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="819a7-115">需求</span><span class="sxs-lookup"><span data-stu-id="819a7-115">Requirements</span></span>  
 <span data-ttu-id="819a7-116">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="819a7-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="819a7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="819a7-117">See Also</span></span>  
 [<span data-ttu-id="819a7-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="819a7-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="819a7-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="819a7-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="819a7-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="819a7-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
