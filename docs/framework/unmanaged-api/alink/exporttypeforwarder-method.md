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
ms.openlocfilehash: 0ae4ddd07a2a3d3ab9b5d024eceb43329db96915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787503"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="2c77c-102">ExportTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="2c77c-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="2c77c-103">將類型轉寄站加入至指定元件的類型資料表。</span><span class="sxs-lookup"><span data-stu-id="2c77c-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c77c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c77c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c77c-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c77c-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="2c77c-106">參考型別轉寄站所參考的元件。</span><span class="sxs-lookup"><span data-stu-id="2c77c-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="2c77c-107">要匯出的完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="2c77c-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2c77c-108">`ComType`旗標， `tdPublic`例如`tdNested`或。</span><span class="sxs-lookup"><span data-stu-id="2c77c-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="2c77c-109">這個值可能會傳遞給[DefineExportedType 方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2c77c-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="2c77c-110">接收匯出類型的 token。</span><span class="sxs-lookup"><span data-stu-id="2c77c-110">Receives the token of the exported type.</span></span> <span data-ttu-id="2c77c-111">這只有在發出巢狀型別時才需要。</span><span class="sxs-lookup"><span data-stu-id="2c77c-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c77c-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2c77c-112">Return Value</span></span>  
 <span data-ttu-id="2c77c-113">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="2c77c-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c77c-114">需求</span><span class="sxs-lookup"><span data-stu-id="2c77c-114">Requirements</span></span>  
 <span data-ttu-id="2c77c-115">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="2c77c-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c77c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c77c-116">See also</span></span>

- [<span data-ttu-id="2c77c-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="2c77c-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2c77c-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="2c77c-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2c77c-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="2c77c-119">ALink API</span></span>](index.md)
