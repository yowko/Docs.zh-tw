---
title: SmiOrderProperty.Item 屬性 (Microsoft.SqlServer.Server)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c586d07e8ea0c2ac0b1efb603e8900d681fd0a91
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152661"
---
# <a name="smiorderpropertyitem-property"></a><span data-ttu-id="9dad9-102">SmiOrderProperty.Item 屬性</span><span class="sxs-lookup"><span data-stu-id="9dad9-102">SmiOrderProperty.Item Property</span></span>

<span data-ttu-id="9dad9-103">取得實體的資料行順序。</span><span class="sxs-lookup"><span data-stu-id="9dad9-103">Gets the column order for the entity.</span></span> <span data-ttu-id="9dad9-104">包含此屬性的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="9dad9-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="9dad9-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="9dad9-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="9dad9-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="9dad9-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="9dad9-107">語法</span><span class="sxs-lookup"><span data-stu-id="9dad9-107">Syntax</span></span>

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a><span data-ttu-id="9dad9-108">屬性值</span><span class="sxs-lookup"><span data-stu-id="9dad9-108">Property value</span></span>

<span data-ttu-id="9dad9-109">資料行順序。</span><span class="sxs-lookup"><span data-stu-id="9dad9-109">The column order.</span></span>

## <a name="remarks"></a><span data-ttu-id="9dad9-110">備註</span><span class="sxs-lookup"><span data-stu-id="9dad9-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="9dad9-111">`SmiOrderProperty.Item`屬性內部，且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="9dad9-111">The `SmiOrderProperty.Item` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9dad9-112">在生產環境應用程式中任何情況下，Microsoft 不支援這個屬性的使用。</span><span class="sxs-lookup"><span data-stu-id="9dad9-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9dad9-113">需求</span><span class="sxs-lookup"><span data-stu-id="9dad9-113">Requirements</span></span>

<span data-ttu-id="9dad9-114">**命名空間︰** <xref:Microsoft.SqlServer.Server></span><span class="sxs-lookup"><span data-stu-id="9dad9-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span></span>

<span data-ttu-id="9dad9-115">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="9dad9-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="9dad9-116">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="9dad9-116">**.NET Framework versions:** Available since 2.0.</span></span>