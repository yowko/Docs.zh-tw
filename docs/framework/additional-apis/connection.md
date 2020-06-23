---
title: Connection 類別（System.Net）
description: 瞭解 .NET 中的 Connection 類別。 這個類別會剖析伺服器回應、佇列要求和管線要求。 它是在 System.NET 命名空間中。
ms.date: 05/01/2017
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
ms.openlocfilehash: cb28724ed782fc5395dc74e9c59249ebdea44ddf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989835"
---
# <a name="connection-class"></a><span data-ttu-id="9530d-105">Connection 類別</span><span class="sxs-lookup"><span data-stu-id="9530d-105">Connection Class</span></span>

<span data-ttu-id="9530d-106">類別會剖析 `Connection` 伺服器回應、佇列要求和管線要求。</span><span class="sxs-lookup"><span data-stu-id="9530d-106">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="9530d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="9530d-107">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="9530d-108">`Connection`類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="9530d-108">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9530d-109">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="9530d-109">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9530d-110">需求</span><span class="sxs-lookup"><span data-stu-id="9530d-110">Requirements</span></span>

<span data-ttu-id="9530d-111">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="9530d-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="9530d-112">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="9530d-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="9530d-113">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="9530d-113">**.NET Framework versions:** Available since 2.0.</span></span>
