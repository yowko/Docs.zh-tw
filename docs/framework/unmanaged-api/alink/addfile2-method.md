---
title: AddFile2 方法
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: cff6707496c7d9657796deb8bf6fa9165ff295a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717080"
---
# <a name="addfile2-method"></a><span data-ttu-id="c9036-102">AddFile2 方法</span><span class="sxs-lookup"><span data-stu-id="c9036-102">AddFile2 Method</span></span>

<span data-ttu-id="c9036-103">將檔案加入至元件。</span><span class="sxs-lookup"><span data-stu-id="c9036-103">Adds files to the assembly.</span></span> <span data-ttu-id="c9036-104">也可以用來建立未系結的模組。</span><span class="sxs-lookup"><span data-stu-id="c9036-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9036-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9036-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9036-106">參數</span><span class="sxs-lookup"><span data-stu-id="c9036-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c9036-107">要加入檔案的元件識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9036-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="c9036-108">要加入的檔案名。</span><span class="sxs-lookup"><span data-stu-id="c9036-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c9036-109">COM + `FileDef` 旗標 `ffContainsNoMetaData` ，例如和 `ffWriteable` 。</span><span class="sxs-lookup"><span data-stu-id="c9036-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="c9036-110">`dwFlags` 會傳遞至 [DefineFile 方法](../metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c9036-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c9036-111">介面 [IMetaDataEmit2 介面](../metadata/imetadataemit2-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="c9036-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c9036-112">接收要加入之檔案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9036-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9036-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9036-113">Return Value</span></span>  

 <span data-ttu-id="c9036-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c9036-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9036-115">需求</span><span class="sxs-lookup"><span data-stu-id="c9036-115">Requirements</span></span>  

 <span data-ttu-id="c9036-116">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="c9036-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9036-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9036-117">See also</span></span>

- [<span data-ttu-id="c9036-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c9036-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c9036-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c9036-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c9036-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="c9036-120">ALink API</span></span>](index.md)
