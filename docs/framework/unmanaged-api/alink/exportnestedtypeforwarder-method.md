---
title: "ExportNestedTypeForwarder 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportNestedTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedTypeForwarder
helpviewer_keywords: ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eee41e9f71d600a74cc9f74b538ad9e215f0d905
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="c8e76-102">ExportNestedTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="c8e76-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="c8e76-103">將指定的組件的型別資料表中的巢狀類型的類型轉送子。</span><span class="sxs-lookup"><span data-stu-id="c8e76-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e76-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8e76-104">Syntax</span></span>  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8e76-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8e76-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c8e76-106">若要從匯出的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="c8e76-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c8e76-107">語彙基元或組件的檔案識別碼定義類型的檔案。</span><span class="sxs-lookup"><span data-stu-id="c8e76-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="c8e76-108">類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c8e76-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="c8e76-109">父類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c8e76-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="c8e76-110">若要匯出的完整限定的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="c8e76-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c8e76-111">`ComType`旗標，例如`tdPublic`或`tdNested`。</span><span class="sxs-lookup"><span data-stu-id="c8e76-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="c8e76-112">接收匯出類型的語彙的基元。</span><span class="sxs-lookup"><span data-stu-id="c8e76-112">Receives token of export type.</span></span> <span data-ttu-id="c8e76-113">這是才需要發出巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="c8e76-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8e76-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="c8e76-114">Return Value</span></span>  
 <span data-ttu-id="c8e76-115">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c8e76-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8e76-116">需求</span><span class="sxs-lookup"><span data-stu-id="c8e76-116">Requirements</span></span>  
 <span data-ttu-id="c8e76-117">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="c8e76-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e76-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8e76-118">See Also</span></span>  
 [<span data-ttu-id="c8e76-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c8e76-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c8e76-120">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c8e76-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c8e76-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="c8e76-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
