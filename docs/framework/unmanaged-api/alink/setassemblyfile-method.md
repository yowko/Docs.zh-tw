---
title: SetAssemblyFile 方法
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d341aca7c96e5932a1fc155ccaee17ce6585da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776997"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="110ec-102">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="110ec-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="110ec-103">指派要建立之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="110ec-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="110ec-104">未在產生未系結模組時使用。</span><span class="sxs-lookup"><span data-stu-id="110ec-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110ec-105">語法</span><span class="sxs-lookup"><span data-stu-id="110ec-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="110ec-106">參數</span><span class="sxs-lookup"><span data-stu-id="110ec-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="110ec-107">資訊清單檔的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="110ec-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="110ec-108">[IMetaDataEmit 介面](../metadata/imetadataemit-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="110ec-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="110ec-109">[AssemblyFlags 列舉](../metadata/assemblyflags-enumeration.md)中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="110ec-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="110ec-110">產生之元件的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="110ec-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="110ec-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="110ec-111">Return Value</span></span>  
 <span data-ttu-id="110ec-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="110ec-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="110ec-113">需求</span><span class="sxs-lookup"><span data-stu-id="110ec-113">Requirements</span></span>  
 <span data-ttu-id="110ec-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="110ec-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110ec-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="110ec-115">See also</span></span>

- [<span data-ttu-id="110ec-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="110ec-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="110ec-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="110ec-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="110ec-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="110ec-118">ALink API</span></span>](index.md)
