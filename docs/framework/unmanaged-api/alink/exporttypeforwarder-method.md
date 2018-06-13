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
ms.openlocfilehash: 5b28c18d55b91d6315003229295ab0e6781be183
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406301"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="77648-102">ExportTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="77648-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="77648-103">將指定的組件的型別資料表中的類型轉送子。</span><span class="sxs-lookup"><span data-stu-id="77648-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77648-104">語法</span><span class="sxs-lookup"><span data-stu-id="77648-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77648-105">參數</span><span class="sxs-lookup"><span data-stu-id="77648-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="77648-106">將類型轉送子所參考之組件參考。</span><span class="sxs-lookup"><span data-stu-id="77648-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="77648-107">若要匯出的完整限定的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="77648-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="77648-108">`ComType` 旗標，例如`tdPublic`或`tdNested`。</span><span class="sxs-lookup"><span data-stu-id="77648-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="77648-109">此值可能會傳遞至[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="77648-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="77648-110">接收匯出的類型語彙的基元。</span><span class="sxs-lookup"><span data-stu-id="77648-110">Receives the token of the exported type.</span></span> <span data-ttu-id="77648-111">這是才需要發出巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="77648-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77648-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="77648-112">Return Value</span></span>  
 <span data-ttu-id="77648-113">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="77648-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77648-114">需求</span><span class="sxs-lookup"><span data-stu-id="77648-114">Requirements</span></span>  
 <span data-ttu-id="77648-115">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="77648-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77648-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77648-116">See Also</span></span>  
 [<span data-ttu-id="77648-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="77648-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="77648-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="77648-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="77648-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="77648-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
