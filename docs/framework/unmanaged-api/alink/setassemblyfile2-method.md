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
ms.openlocfilehash: aba11ccd61b65d2a779b39db8e0e082cf4d4015b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787225"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="d0e5c-102">SetAssemblyFile2 方法</span><span class="sxs-lookup"><span data-stu-id="d0e5c-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="d0e5c-103">設定新元件的名稱和選項。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="d0e5c-104">當您產生未系結的模組時，請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e5c-105">語法</span><span class="sxs-lookup"><span data-stu-id="d0e5c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0e5c-106">參數</span><span class="sxs-lookup"><span data-stu-id="d0e5c-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="d0e5c-107">資訊清單檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="d0e5c-108">此檔案的[IMetaDataEmit2 介面](../metadata/imetadataemit2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="d0e5c-109">[AssemblyFlags 列舉](../metadata/assemblyflags-enumeration.md)所表示的選項。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="d0e5c-110">接收所結構化元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0e5c-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d0e5c-111">Return Value</span></span>  
 <span data-ttu-id="d0e5c-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0e5c-113">需求</span><span class="sxs-lookup"><span data-stu-id="d0e5c-113">Requirements</span></span>  
 <span data-ttu-id="d0e5c-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e5c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0e5c-115">See also</span></span>

- [<span data-ttu-id="d0e5c-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="d0e5c-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d0e5c-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="d0e5c-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d0e5c-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="d0e5c-118">ALink API</span></span>](index.md)
