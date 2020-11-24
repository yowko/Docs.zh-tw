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
ms.openlocfilehash: 2070d1ec2aec80638c20c764eed5086c4a42e0fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676357"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="c6cba-102">EmitAssemblyCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="c6cba-102">EmitAssemblyCustomAttribute Method</span></span>

<span data-ttu-id="c6cba-103">呼叫以設定元件層級的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="c6cba-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6cba-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6cba-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c6cba-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6cba-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c6cba-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c6cba-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c6cba-107">定義屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="c6cba-107">File that defiles the attribute.</span></span> <span data-ttu-id="c6cba-108">如果未指出未系結 `AssemblyID` 的 .netmodule，則可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="c6cba-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c6cba-109">自訂屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="c6cba-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="c6cba-110">自訂值資料。</span><span class="sxs-lookup"><span data-stu-id="c6cba-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="c6cba-111">自訂值資料的長度。</span><span class="sxs-lookup"><span data-stu-id="c6cba-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="c6cba-112">如果自訂屬性與元件簽署相關，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c6cba-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="c6cba-113">如果要發出多個屬性，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c6cba-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6cba-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="c6cba-114">Return Value</span></span>  

 <span data-ttu-id="c6cba-115">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c6cba-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6cba-116">需求</span><span class="sxs-lookup"><span data-stu-id="c6cba-116">Requirements</span></span>  

 <span data-ttu-id="c6cba-117">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="c6cba-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6cba-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6cba-118">See also</span></span>

- [<span data-ttu-id="c6cba-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c6cba-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c6cba-120">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c6cba-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c6cba-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="c6cba-121">ALink API</span></span>](index.md)
