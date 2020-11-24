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
ms.openlocfilehash: 4e6ceabf37056bfc25247266be2c7801cb0e13e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684768"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="24bdf-102">ExportTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="24bdf-102">ExportTypeForwarder Method</span></span>

<span data-ttu-id="24bdf-103">將型別轉寄站加入至指定元件的型別資料表。</span><span class="sxs-lookup"><span data-stu-id="24bdf-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24bdf-104">語法</span><span class="sxs-lookup"><span data-stu-id="24bdf-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="24bdf-105">參數</span><span class="sxs-lookup"><span data-stu-id="24bdf-105">Parameters</span></span>  

 `tkAssemblyRef`  
 <span data-ttu-id="24bdf-106">型別轉寄站所參考之元件的參考。</span><span class="sxs-lookup"><span data-stu-id="24bdf-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="24bdf-107">要匯出的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="24bdf-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="24bdf-108">`ComType` 旗標，例如 `tdPublic` 或 `tdNested` 。</span><span class="sxs-lookup"><span data-stu-id="24bdf-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="24bdf-109">這個值可以傳遞給 [DefineExportedType 方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="24bdf-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="24bdf-110">接收匯出類型的標記。</span><span class="sxs-lookup"><span data-stu-id="24bdf-110">Receives the token of the exported type.</span></span> <span data-ttu-id="24bdf-111">只有發出巢狀型別時，才需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="24bdf-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24bdf-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="24bdf-112">Return Value</span></span>  

 <span data-ttu-id="24bdf-113">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="24bdf-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24bdf-114">需求</span><span class="sxs-lookup"><span data-stu-id="24bdf-114">Requirements</span></span>  

 <span data-ttu-id="24bdf-115">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="24bdf-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24bdf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24bdf-116">See also</span></span>

- [<span data-ttu-id="24bdf-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="24bdf-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="24bdf-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="24bdf-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="24bdf-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="24bdf-119">ALink API</span></span>](index.md)
