---
title: "ExportType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportType
api_location: alink.dll
api_type: COM
f1_keywords: ExportType
helpviewer_keywords: ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3f7bd3991fa57f11674b7ef0b9b62d12376fa765
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="exporttype-method"></a><span data-ttu-id="b7f28-102">ExportType 方法</span><span class="sxs-lookup"><span data-stu-id="b7f28-102">ExportType Method</span></span>
<span data-ttu-id="b7f28-103">指定類型為可匯出。</span><span class="sxs-lookup"><span data-stu-id="b7f28-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7f28-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7f28-104">Syntax</span></span>  
  
```  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7f28-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7f28-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b7f28-106">若要從匯出的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="b7f28-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b7f28-107">語彙基元或組件的檔案識別碼定義可匯出類型的檔案。</span><span class="sxs-lookup"><span data-stu-id="b7f28-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="b7f28-108">成可匯出的類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b7f28-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="b7f28-109">成可匯出的完整限定的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="b7f28-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b7f28-110">`ComType`旗標，例如`tdPublic`或`tdNested`。</span><span class="sxs-lookup"><span data-stu-id="b7f28-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="b7f28-111">此參數可能會傳遞至[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="b7f28-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="b7f28-112">接收匯出類型的語彙的基元。</span><span class="sxs-lookup"><span data-stu-id="b7f28-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7f28-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="b7f28-113">Return Value</span></span>  
 <span data-ttu-id="b7f28-114">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="b7f28-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7f28-115">需求</span><span class="sxs-lookup"><span data-stu-id="b7f28-115">Requirements</span></span>  
 <span data-ttu-id="b7f28-116">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="b7f28-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f28-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7f28-117">See Also</span></span>  
 [<span data-ttu-id="b7f28-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="b7f28-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b7f28-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="b7f28-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b7f28-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="b7f28-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
