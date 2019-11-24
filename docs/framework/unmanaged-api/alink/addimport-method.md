---
title: AddImport 方法
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 52e52ac62e2dcfeb182da3014a863409f640274e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446650"
---
# <a name="addimport-method"></a><span data-ttu-id="73201-102">AddImport 方法</span><span class="sxs-lookup"><span data-stu-id="73201-102">AddImport Method</span></span>
<span data-ttu-id="73201-103">Adds imports to the assembly.</span><span class="sxs-lookup"><span data-stu-id="73201-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73201-104">語法</span><span class="sxs-lookup"><span data-stu-id="73201-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="73201-105">參數</span><span class="sxs-lookup"><span data-stu-id="73201-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="73201-106">Unique ID of assembly to be augmented.</span><span class="sxs-lookup"><span data-stu-id="73201-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="73201-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span><span class="sxs-lookup"><span data-stu-id="73201-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="73201-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="73201-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="73201-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="73201-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="73201-110">Pointer to token that receives the ID for the resulting file.</span><span class="sxs-lookup"><span data-stu-id="73201-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73201-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="73201-111">Return Value</span></span>  
 <span data-ttu-id="73201-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="73201-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73201-113">需求</span><span class="sxs-lookup"><span data-stu-id="73201-113">Requirements</span></span>  
 <span data-ttu-id="73201-114">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="73201-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73201-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="73201-115">See also</span></span>

- [<span data-ttu-id="73201-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="73201-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="73201-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="73201-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="73201-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="73201-118">ALink API</span></span>](index.md)
