---
title: ExportTypeForwarder 方法
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f97f46595f43c7576c499c6b9944f7e3509662fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742013"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="d415e-102">ExportTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="d415e-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="d415e-103">將指定的組件的型別表中的類型轉送子。</span><span class="sxs-lookup"><span data-stu-id="d415e-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d415e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d415e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d415e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d415e-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="d415e-106">類型轉送子所參考之組件參考。</span><span class="sxs-lookup"><span data-stu-id="d415e-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="d415e-107">若要匯出的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d415e-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d415e-108">`ComType` 這類旗標`tdPublic`或`tdNested`。</span><span class="sxs-lookup"><span data-stu-id="d415e-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="d415e-109">這個值可能會傳遞至[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d415e-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="d415e-110">收到之匯出型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="d415e-110">Receives the token of the exported type.</span></span> <span data-ttu-id="d415e-111">這是才需要發出巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="d415e-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d415e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d415e-112">Return Value</span></span>  
 <span data-ttu-id="d415e-113">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d415e-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d415e-114">需求</span><span class="sxs-lookup"><span data-stu-id="d415e-114">Requirements</span></span>  
 <span data-ttu-id="d415e-115">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="d415e-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d415e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d415e-116">See also</span></span>

- [<span data-ttu-id="d415e-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="d415e-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d415e-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="d415e-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d415e-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="d415e-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
