---
title: ExportNestedType 方法
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: fded6b95144d4088a2abc8dfcc4ef8eda331c34f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438430"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="c8110-102">ExportNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="c8110-102">ExportNestedType Method</span></span>
<span data-ttu-id="c8110-103">Specifies nested types as exportable.</span><span class="sxs-lookup"><span data-stu-id="c8110-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="c8110-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span><span class="sxs-lookup"><span data-stu-id="c8110-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8110-105">語法</span><span class="sxs-lookup"><span data-stu-id="c8110-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="c8110-106">參數</span><span class="sxs-lookup"><span data-stu-id="c8110-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c8110-107">ID of assembly to export from.</span><span class="sxs-lookup"><span data-stu-id="c8110-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c8110-108">File token or Assembly of file that defines the type to be made exportable.</span><span class="sxs-lookup"><span data-stu-id="c8110-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="c8110-109">Type token of type to be made exportable.</span><span class="sxs-lookup"><span data-stu-id="c8110-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="c8110-110">Token of parent type.</span><span class="sxs-lookup"><span data-stu-id="c8110-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="c8110-111">Fully qualified type name to export.</span><span class="sxs-lookup"><span data-stu-id="c8110-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c8110-112">`ComType` flags such as `tdPublic` or `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="c8110-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="c8110-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="c8110-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="c8110-114">Receives token for exported type.</span><span class="sxs-lookup"><span data-stu-id="c8110-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8110-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="c8110-115">Return Value</span></span>  
 <span data-ttu-id="c8110-116">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="c8110-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8110-117">需求</span><span class="sxs-lookup"><span data-stu-id="c8110-117">Requirements</span></span>  
 <span data-ttu-id="c8110-118">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="c8110-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8110-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8110-119">See also</span></span>

- [<span data-ttu-id="c8110-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c8110-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c8110-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c8110-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c8110-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="c8110-122">ALink API</span></span>](index.md)
