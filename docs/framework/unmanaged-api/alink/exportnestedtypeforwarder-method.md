---
title: ExportNestedTypeForwarder 方法
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25b7a708bb2f16433d9de9b5fc1c178cb48874a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658464"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="f8735-102">ExportNestedTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="f8735-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="f8735-103">將指定的組件的型別表中的巢狀類型的類型轉送子。</span><span class="sxs-lookup"><span data-stu-id="f8735-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8735-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8735-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f8735-105">參數</span><span class="sxs-lookup"><span data-stu-id="f8735-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f8735-106">若要從匯出的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="f8735-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f8735-107">語彙基元或組件檔案的檔案識別碼所定義的型別。</span><span class="sxs-lookup"><span data-stu-id="f8735-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="f8735-108">類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f8735-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="f8735-109">父型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="f8735-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="f8735-110">若要匯出的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f8735-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f8735-111">`ComType` 這類旗標`tdPublic`或`tdNested`。</span><span class="sxs-lookup"><span data-stu-id="f8735-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="f8735-112">接收匯出類型的語彙的基元。</span><span class="sxs-lookup"><span data-stu-id="f8735-112">Receives token of export type.</span></span> <span data-ttu-id="f8735-113">這是才需要發出巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="f8735-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8735-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="f8735-114">Return Value</span></span>  
 <span data-ttu-id="f8735-115">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f8735-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8735-116">需求</span><span class="sxs-lookup"><span data-stu-id="f8735-116">Requirements</span></span>  
 <span data-ttu-id="f8735-117">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="f8735-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8735-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8735-118">See also</span></span>
- [<span data-ttu-id="f8735-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="f8735-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f8735-120">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="f8735-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f8735-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="f8735-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
