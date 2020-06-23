---
title: WebHeaderCollection. AddInternal 方法（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990306"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="32247-102">WebHeaderCollection. AddInternal 方法</span><span class="sxs-lookup"><span data-stu-id="32247-102">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="32247-103">將具有指定之名稱和值的新標頭加入至集合，略過檢查。</span><span class="sxs-lookup"><span data-stu-id="32247-103">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="32247-104">這個方法是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="32247-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="32247-105">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="32247-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="32247-106">參數</span><span class="sxs-lookup"><span data-stu-id="32247-106">Parameters</span></span>

- <span data-ttu-id="32247-107">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="32247-107">`name` <xref:System.String></span></span>

  <span data-ttu-id="32247-108">標頭的名稱。</span><span class="sxs-lookup"><span data-stu-id="32247-108">The name of the header.</span></span>

- <span data-ttu-id="32247-109">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="32247-109">`value` <xref:System.String></span></span>

  <span data-ttu-id="32247-110">標頭的值。</span><span class="sxs-lookup"><span data-stu-id="32247-110">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="32247-111">需求</span><span class="sxs-lookup"><span data-stu-id="32247-111">Requirements</span></span>

<span data-ttu-id="32247-112">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="32247-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="32247-113">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="32247-113">**Assembly:** System (in System.dll)</span></span>
