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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff159cf794d566be6478ef890c769a0ac72c9b25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789945"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="8e1ab-102">ExportNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="8e1ab-102">ExportNestedType Method</span></span>
<span data-ttu-id="8e1ab-103">指定巢狀型別為可匯出。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="8e1ab-104">[ExportType 方法](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md)也可以匯出巢狀類型，但這個方法會比較快。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e1ab-105">語法</span><span class="sxs-lookup"><span data-stu-id="8e1ab-105">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="8e1ab-106">參數</span><span class="sxs-lookup"><span data-stu-id="8e1ab-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8e1ab-107">若要從匯出的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8e1ab-108">檔案的語彙基元或組件的檔案，定義成可匯出的型別。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="8e1ab-109">可匯出型別的型別語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="8e1ab-110">父型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="8e1ab-111">若要匯出的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8e1ab-112">`ComType` 這類旗標`tdPublic`或`tdNested`。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="8e1ab-113">這個值可能會傳遞至[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="8e1ab-114">接收匯出之類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e1ab-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e1ab-115">Return Value</span></span>  
 <span data-ttu-id="8e1ab-116">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8e1ab-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e1ab-117">需求</span><span class="sxs-lookup"><span data-stu-id="8e1ab-117">Requirements</span></span>  
 <span data-ttu-id="8e1ab-118">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="8e1ab-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e1ab-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e1ab-119">See also</span></span>

- [<span data-ttu-id="8e1ab-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="8e1ab-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8e1ab-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="8e1ab-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8e1ab-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="8e1ab-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
