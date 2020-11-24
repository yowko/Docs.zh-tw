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
ms.openlocfilehash: 34439b7c01dee7d7789d989b58e8944c6282b71b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676383"
---
# <a name="embedresource-method"></a><span data-ttu-id="8908f-102">EmbedResource 方法</span><span class="sxs-lookup"><span data-stu-id="8908f-102">EmbedResource Method</span></span>

<span data-ttu-id="8908f-103">宣告內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="8908f-103">Declares an embedded resource.</span></span> <span data-ttu-id="8908f-104">這個方法不會實際內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="8908f-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8908f-105">語法</span><span class="sxs-lookup"><span data-stu-id="8908f-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8908f-106">參數</span><span class="sxs-lookup"><span data-stu-id="8908f-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="8908f-107">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8908f-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8908f-108">包含資源之檔案的檔案 token 或元件識別碼。</span><span class="sxs-lookup"><span data-stu-id="8908f-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="8908f-109">資源名稱。</span><span class="sxs-lookup"><span data-stu-id="8908f-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="8908f-110">從 RVA 開始的資源位移。</span><span class="sxs-lookup"><span data-stu-id="8908f-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8908f-111">協助工具旗標 `mrPublic` ，例如和 `mrPrivate` 。</span><span class="sxs-lookup"><span data-stu-id="8908f-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="8908f-112">這些旗標可傳遞至 [DefineExportedType 方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="8908f-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8908f-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="8908f-113">Return Value</span></span>  

 <span data-ttu-id="8908f-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8908f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8908f-115">需求</span><span class="sxs-lookup"><span data-stu-id="8908f-115">Requirements</span></span>  

 <span data-ttu-id="8908f-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="8908f-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8908f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8908f-117">See also</span></span>

- [<span data-ttu-id="8908f-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="8908f-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8908f-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="8908f-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8908f-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="8908f-120">ALink API</span></span>](index.md)
