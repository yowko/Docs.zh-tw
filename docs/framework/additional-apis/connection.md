---
title: Connection 類別（System.Net）
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
ms.openlocfilehash: e9e0f4eed5eb4a7efd27177ab65551afa87fb7f6
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215082"
---
# <a name="connection-class"></a><span data-ttu-id="084b4-102">Connection 類別</span><span class="sxs-lookup"><span data-stu-id="084b4-102">Connection Class</span></span>

<span data-ttu-id="084b4-103">`Connection` 類別會剖析伺服器回應、佇列要求和管線要求。</span><span class="sxs-lookup"><span data-stu-id="084b4-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="084b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="084b4-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="084b4-105">`Connection` 類別是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="084b4-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="084b4-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="084b4-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="084b4-107">需求</span><span class="sxs-lookup"><span data-stu-id="084b4-107">Requirements</span></span>

<span data-ttu-id="084b4-108">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="084b4-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="084b4-109">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="084b4-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="084b4-110">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="084b4-110">**.NET Framework versions:** Available since 2.0.</span></span>
