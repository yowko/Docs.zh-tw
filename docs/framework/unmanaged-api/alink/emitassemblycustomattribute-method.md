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
ms.openlocfilehash: 67073f04cfe981dd383369029d9a4b436929a0a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117841"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="030df-102">EmitAssemblyCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="030df-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="030df-103">呼叫以設定組件層級的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="030df-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="030df-104">語法</span><span class="sxs-lookup"><span data-stu-id="030df-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="030df-105">參數</span><span class="sxs-lookup"><span data-stu-id="030df-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="030df-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="030df-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="030df-107">定義屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="030df-107">File that defiles the attribute.</span></span> <span data-ttu-id="030df-108">可以是 NULL，如果`AssemblyID`不會指出未繫結的 netmodule。</span><span class="sxs-lookup"><span data-stu-id="030df-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="030df-109">自訂屬性型別。</span><span class="sxs-lookup"><span data-stu-id="030df-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="030df-110">自訂值的資料。</span><span class="sxs-lookup"><span data-stu-id="030df-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="030df-111">自訂數值資料的長度。</span><span class="sxs-lookup"><span data-stu-id="030df-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="030df-112">如果簽章的組件與相關的自訂屬性，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="030df-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="030df-113">如果多個屬性，就會發出，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="030df-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="030df-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="030df-114">Return Value</span></span>  
 <span data-ttu-id="030df-115">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="030df-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="030df-116">需求</span><span class="sxs-lookup"><span data-stu-id="030df-116">Requirements</span></span>  
 <span data-ttu-id="030df-117">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="030df-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030df-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="030df-118">See also</span></span>

- [<span data-ttu-id="030df-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="030df-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="030df-120">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="030df-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="030df-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="030df-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
