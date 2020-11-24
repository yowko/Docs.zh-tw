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
ms.openlocfilehash: b8db08b22765bac0ed2fe058db49d6882b8d22df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684794"
---
# <a name="exporttype-method"></a><span data-ttu-id="c0e6b-102">ExportType 方法</span><span class="sxs-lookup"><span data-stu-id="c0e6b-102">ExportType Method</span></span>

<span data-ttu-id="c0e6b-103">指定可匯出的型別。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0e6b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0e6b-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0e6b-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c0e6b-106">要匯出之元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c0e6b-107">定義可匯出類型之檔案的檔案 token 或元件識別碼。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="c0e6b-108">要成為可匯出的型別權杖。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="c0e6b-109">要成為可匯出的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c0e6b-110">`ComType` 旗標，例如 `tdPublic` 或 `tdNested` 。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="c0e6b-111">這個參數可以傳遞給 [DefineExportedType 方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-111">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="c0e6b-112">接收匯出類型的權杖。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0e6b-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="c0e6b-113">Return Value</span></span>  

 <span data-ttu-id="c0e6b-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c0e6b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0e6b-115">需求</span><span class="sxs-lookup"><span data-stu-id="c0e6b-115">Requirements</span></span>  

 <span data-ttu-id="c0e6b-116">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="c0e6b-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e6b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0e6b-117">See also</span></span>

- [<span data-ttu-id="c0e6b-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c0e6b-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c0e6b-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c0e6b-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c0e6b-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="c0e6b-120">ALink API</span></span>](index.md)
