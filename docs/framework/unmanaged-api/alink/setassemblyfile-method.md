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
ms.openlocfilehash: a19762cbec91871d7af617957896e4ee34944fba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132703"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="803ed-102">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="803ed-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="803ed-103">指定要建置的組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="803ed-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="803ed-104">不適用於產生繫結的模組時使用。</span><span class="sxs-lookup"><span data-stu-id="803ed-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="803ed-105">語法</span><span class="sxs-lookup"><span data-stu-id="803ed-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="803ed-106">參數</span><span class="sxs-lookup"><span data-stu-id="803ed-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="803ed-107">資訊清單檔案的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="803ed-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="803ed-108">指標[IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="803ed-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="803ed-109">中所定義的旗標[AssemblyFlags 列舉](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="803ed-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="803ed-110">產生的組件的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="803ed-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="803ed-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="803ed-111">Return Value</span></span>  
 <span data-ttu-id="803ed-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="803ed-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="803ed-113">需求</span><span class="sxs-lookup"><span data-stu-id="803ed-113">Requirements</span></span>  
 <span data-ttu-id="803ed-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="803ed-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="803ed-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="803ed-115">See also</span></span>

- [<span data-ttu-id="803ed-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="803ed-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="803ed-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="803ed-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="803ed-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="803ed-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
