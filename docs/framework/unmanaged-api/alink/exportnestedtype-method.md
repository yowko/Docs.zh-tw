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
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179406"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="d8f32-102">ExportNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="d8f32-102">ExportNestedType Method</span></span>
<span data-ttu-id="d8f32-103">將巢狀型別指定為可匯出類型。</span><span class="sxs-lookup"><span data-stu-id="d8f32-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="d8f32-104">[匯出類型方法](exporttype-method.md)還可以匯出巢狀型別，但此方法更快。</span><span class="sxs-lookup"><span data-stu-id="d8f32-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f32-105">語法</span><span class="sxs-lookup"><span data-stu-id="d8f32-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d8f32-106">參數</span><span class="sxs-lookup"><span data-stu-id="d8f32-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d8f32-107">要匯出的程式集的 ID。</span><span class="sxs-lookup"><span data-stu-id="d8f32-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d8f32-108">檔權杖或檔程式集，用於定義要匯出的類型。</span><span class="sxs-lookup"><span data-stu-id="d8f32-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="d8f32-109">類型權杖，使可匯出。</span><span class="sxs-lookup"><span data-stu-id="d8f32-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="d8f32-110">父類型的權杖。</span><span class="sxs-lookup"><span data-stu-id="d8f32-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="d8f32-111">要匯出的完全限定類型名稱。</span><span class="sxs-lookup"><span data-stu-id="d8f32-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d8f32-112">`ComType`標誌，如`tdPublic``tdNested`或 。</span><span class="sxs-lookup"><span data-stu-id="d8f32-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="d8f32-113">此值可以傳遞給[定義匯出類型方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f32-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="d8f32-114">接收匯出類型的權杖。</span><span class="sxs-lookup"><span data-stu-id="d8f32-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8f32-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="d8f32-115">Return Value</span></span>  
 <span data-ttu-id="d8f32-116">如果方法成功，則返回S_OK。</span><span class="sxs-lookup"><span data-stu-id="d8f32-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8f32-117">需求</span><span class="sxs-lookup"><span data-stu-id="d8f32-117">Requirements</span></span>  
 <span data-ttu-id="d8f32-118">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="d8f32-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f32-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8f32-119">See also</span></span>

- [<span data-ttu-id="d8f32-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="d8f32-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d8f32-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="d8f32-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d8f32-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="d8f32-122">ALink API</span></span>](index.md)
