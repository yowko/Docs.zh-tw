---
title: EmitAssemblyCustomAttribute 方法
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69914bce7ed322d90cfbd03dd611e2b745dfe066
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470025"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="4b5af-102">EmitAssemblyCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="4b5af-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="4b5af-103">呼叫以設定組件層級的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="4b5af-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b5af-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b5af-104">Syntax</span></span>  
  
```  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b5af-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b5af-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4b5af-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b5af-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4b5af-107">定義屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="4b5af-107">File that defiles the attribute.</span></span> <span data-ttu-id="4b5af-108">可以是 NULL，如果`AssemblyID`不會指出未繫結的 netmodule。</span><span class="sxs-lookup"><span data-stu-id="4b5af-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="4b5af-109">自訂屬性型別。</span><span class="sxs-lookup"><span data-stu-id="4b5af-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="4b5af-110">自訂值的資料。</span><span class="sxs-lookup"><span data-stu-id="4b5af-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="4b5af-111">自訂數值資料的長度。</span><span class="sxs-lookup"><span data-stu-id="4b5af-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="4b5af-112">如果簽章的組件與相關的自訂屬性，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4b5af-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="4b5af-113">如果多個屬性，就會發出，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="4b5af-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b5af-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b5af-114">Return Value</span></span>  
 <span data-ttu-id="4b5af-115">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4b5af-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b5af-116">需求</span><span class="sxs-lookup"><span data-stu-id="4b5af-116">Requirements</span></span>  
 <span data-ttu-id="4b5af-117">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="4b5af-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5af-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b5af-118">See also</span></span>
- [<span data-ttu-id="4b5af-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4b5af-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="4b5af-120">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4b5af-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="4b5af-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="4b5af-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
