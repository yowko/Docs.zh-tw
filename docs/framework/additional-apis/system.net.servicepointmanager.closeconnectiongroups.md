---
title: ServicePointManager. CloseConnectionGroups 方法（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990309"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="713a5-102">ServicePointManager. CloseConnectionGroups 方法</span><span class="sxs-lookup"><span data-stu-id="713a5-102">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="713a5-103">逐一查看所有服務點，並關閉具有指定之名稱的連接群組。</span><span class="sxs-lookup"><span data-stu-id="713a5-103">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="713a5-104">這個方法是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="713a5-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="713a5-105">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="713a5-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="713a5-106">參數</span><span class="sxs-lookup"><span data-stu-id="713a5-106">Parameters</span></span>

<span data-ttu-id="713a5-107">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="713a5-107">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="713a5-108">要關閉之連接群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="713a5-108">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="713a5-109">需求</span><span class="sxs-lookup"><span data-stu-id="713a5-109">Requirements</span></span>

<span data-ttu-id="713a5-110">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="713a5-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="713a5-111">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="713a5-111">**Assembly:** System (in System.dll)</span></span>
