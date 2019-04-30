---
title: SetAssemblyFile2 方法
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59bfc6785d3ad195e219afc323b7fdb513d8fefc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949054"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="0fe72-102">SetAssemblyFile2 方法</span><span class="sxs-lookup"><span data-stu-id="0fe72-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="0fe72-103">設定的名稱和新的組件的選項。</span><span class="sxs-lookup"><span data-stu-id="0fe72-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="0fe72-104">當您產生未繫結的模組時，請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="0fe72-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe72-105">語法</span><span class="sxs-lookup"><span data-stu-id="0fe72-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fe72-106">參數</span><span class="sxs-lookup"><span data-stu-id="0fe72-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="0fe72-107">資訊清單檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0fe72-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="0fe72-108">[IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)介面，此檔案。</span><span class="sxs-lookup"><span data-stu-id="0fe72-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="0fe72-109">所表示的選項[AssemblyFlags 列舉](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe72-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="0fe72-110">接收所建構的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="0fe72-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fe72-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="0fe72-111">Return Value</span></span>  
 <span data-ttu-id="0fe72-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="0fe72-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fe72-113">需求</span><span class="sxs-lookup"><span data-stu-id="0fe72-113">Requirements</span></span>  
 <span data-ttu-id="0fe72-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="0fe72-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe72-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fe72-115">See also</span></span>

- [<span data-ttu-id="0fe72-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="0fe72-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0fe72-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="0fe72-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0fe72-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="0fe72-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
