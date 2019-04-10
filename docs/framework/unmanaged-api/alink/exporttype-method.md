---
title: ExportType 方法
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95ff27143453e7772b4a463fa66ca039bbb715fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226913"
---
# <a name="exporttype-method"></a><span data-ttu-id="ac830-102">ExportType 方法</span><span class="sxs-lookup"><span data-stu-id="ac830-102">ExportType Method</span></span>
<span data-ttu-id="ac830-103">指定的類型是可匯出。</span><span class="sxs-lookup"><span data-stu-id="ac830-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac830-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac830-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ac830-105">參數</span><span class="sxs-lookup"><span data-stu-id="ac830-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ac830-106">若要從匯出的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac830-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ac830-107">語彙基元或組件檔案的檔案識別碼定義可匯出的類型。</span><span class="sxs-lookup"><span data-stu-id="ac830-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="ac830-108">可匯出的型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="ac830-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="ac830-109">成可匯出的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ac830-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 `ComType` <span data-ttu-id="ac830-110">這類旗標`tdPublic`或`tdNested`。</span><span class="sxs-lookup"><span data-stu-id="ac830-110">flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="ac830-111">這個參數可能會傳遞給[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ac830-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="ac830-112">接收匯出之類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ac830-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac830-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="ac830-113">Return Value</span></span>  
 <span data-ttu-id="ac830-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ac830-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac830-115">需求</span><span class="sxs-lookup"><span data-stu-id="ac830-115">Requirements</span></span>  
 <span data-ttu-id="ac830-116">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="ac830-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac830-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac830-117">See also</span></span>

- [<span data-ttu-id="ac830-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ac830-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ac830-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ac830-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ac830-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="ac830-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
