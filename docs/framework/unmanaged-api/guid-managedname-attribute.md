---
title: GUID_ManagedName 屬性
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bae50f695de81856d4fddcb2af3d1188d896642
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430007"
---
# <a name="guidmanagedname-attribute"></a><span data-ttu-id="c0550-102">GUID_ManagedName 屬性</span><span class="sxs-lookup"><span data-stu-id="c0550-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="c0550-103">定義指定之元件物件模型 (COM) 程式庫的受管理的命名空間名稱的自訂介面屬性。</span><span class="sxs-lookup"><span data-stu-id="c0550-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0550-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0550-104">Syntax</span></span>  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0550-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0550-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="c0550-106">媒體櫃受管理的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="c0550-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="c0550-107">定義</span><span class="sxs-lookup"><span data-stu-id="c0550-107">Definition</span></span>  
 <span data-ttu-id="c0550-108">`GUID_ManagedName` 則定義於 Cor.h，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c0550-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0550-109">備註</span><span class="sxs-lookup"><span data-stu-id="c0550-109">Remarks</span></span>  
 <span data-ttu-id="c0550-110">自訂介面屬性類型程式庫中定義物件之中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c0550-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="c0550-111">使用<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType>或<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType>從屬性擷取受管理的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0550-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="c0550-112">如需詳細資訊，請參閱[介面屬性](/cpp/windows/interface-attributes)Visual c + + 參考文件。</span><span class="sxs-lookup"><span data-stu-id="c0550-112">For more information, see [Interface Attributes](/cpp/windows/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0550-113">範例</span><span class="sxs-lookup"><span data-stu-id="c0550-113">Example</span></span>  
 <span data-ttu-id="c0550-114">下列範例顯示使用程式庫定義`GUID_ManagedName`屬性。</span><span class="sxs-lookup"><span data-stu-id="c0550-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```  
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="c0550-115">需求</span><span class="sxs-lookup"><span data-stu-id="c0550-115">Requirements</span></span>  
 <span data-ttu-id="c0550-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0550-116">**Header:** Cor.h</span></span>
